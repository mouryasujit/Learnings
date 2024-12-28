# This is file for RTkquery setup

## create store.js inside app folder
```bash
import { configureStore } from "@reduxjs/toolkit";
import rootReducer from "./rootReducer";
import { authApi } from "@/features/api/authapi";
import { courseApi } from "@/features/api/courseApi";
export const store = configureStore({
  reducer: rootReducer,
  middleware: (getDefaultMiddleware) =>
    getDefaultMiddleware().concat(authApi.middleware,courseApi.middleware),
});

const intializeApp = async () => {
  await store.dispatch(
    authApi.endpoints.getUser.initiate({}, { forceRefetch: true })
  );
};
intializeApp();
// Infer the `RootState` and `AppDispatch` types from the store itself
export type RootState = ReturnType<typeof store.getState>;
// Inferred type: {posts: PostsState, comments: CommentsState, users: UsersState}
export type AppDispatch = typeof store.dispatch;

```
## Now there only create rootReducers file
```bash
import { combineReducers } from "@reduxjs/toolkit";
import { authApi } from "@/features/api/authApi";
import authReducer from "../features/authSlice";
import { courseApi } from "@/features/api/courseApi";

const rootReducer = combineReducers({
  [authApi.reducerPath]: authApi.reducer,
  [courseApi.reducerPath]:courseApi.reducer,
  auth: authReducer,
});
export default rootReducer;
```

## Now create a features folder->createSLices
```bash
import { createSlice, PayloadAction } from "@reduxjs/toolkit";

interface User {
  _id: string;
  name: string;
  email: string;
  role: string;
  courseEnrolled?: string[];
  photoUrl?: string;
  createdAt: Date;
  updatedAt: Date;
}

interface Inital {
  user: User | null;
  isAuthenticated: boolean;
}
const initialState: Inital = {
  user: null,
  isAuthenticated: false,
};

const authSlice = createSlice({
  name: "auth",
  initialState,
  reducers: {
    isLoggedIn: (state, action: PayloadAction<User>) => {
      state.user = action.payload;
      state.isAuthenticated = true;
    },
    isLoggedOut: (state) => {
      state.user = null;
      state.isAuthenticated = false;
    },
  },
});
export const { isLoggedIn, isLoggedOut } = authSlice.actions;
export default authSlice.reducer;
```
## inside features->api->authAPi(or any other api file eg->courseApi)
```bash
import { createApi, fetchBaseQuery } from "@reduxjs/toolkit/query/react";
import { isLoggedIn, isLoggedOut } from "../authSlice";
// import { register } from "module";

const USER_API = "http://localhost:3000/api/v1/user/";
export const authApi = createApi({
  reducerPath: "authApi",
  baseQuery: fetchBaseQuery({
    baseUrl: USER_API,
    credentials: "include",
  }),
  endpoints: (builder) => ({
    registerUser: builder.mutation({
      query: (inputData) => ({
        url: "register",
        method: "POST",
        body: inputData,
      }),
    }),
    loginUser: builder.mutation({
      query: (inputData) => ({
        url: "login",
        method: "POST",
        body: inputData,
      }),

      async onQueryStarted(_, { queryFulfilled, dispatch }) {
        try {
          const result = await queryFulfilled;
          dispatch(isLoggedIn(result.data));
          console.log("from authApi", result.data);
        } catch (error) {
          console.log(error);
        }
      },
    }),
    logoutUser: builder.mutation({
      query: () => ({
        url: "logout",
        method: "GET",
      }),
      async onQueryStarted(_, { queryFulfilled, dispatch }) {
        try {
          const result = await queryFulfilled;
          dispatch(isLoggedOut());
          console.log(result);
        } catch (error) {
          console.log(error);
        }
      },
    }),
    getUser: builder.query({
      query: () => ({ url: "profile", method: "GET" }),
      async onQueryStarted(_, { queryFulfilled, dispatch }) {
        try {
          const result = await queryFulfilled;
          dispatch(isLoggedIn(result.data));
          console.log("from authApi", result.data);
        } catch (error) {
          console.log(error);
        }
      },
    }),
    updateUser: builder.mutation({
      query: (formData) => ({
        url: "profile/update",
        method: "PUT",
        body: formData,
        credentials: "include",
      }),
    }),
  }),
});

export const {
  useRegisterUserMutation,
  useLoginUserMutation,
  useGetUserQuery,
  useUpdateUserMutation,
  useLogoutUserMutation,
} = authApi;
```
## usage 
- inside any file
  ```bash
     //for mutation hooks
      const [authApi,{isLoading,isSuccess,error,data}]=useRegisterUserMutation({});
      await authApi({    pass necessary parameter specified in app/authApi(or any other file)   }) 
     // for queryHooks
      const {isLoading,isSuccess,error,data}=useuseGetUserQuery({});
```

````
