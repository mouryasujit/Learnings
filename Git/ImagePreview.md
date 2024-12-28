# Using this code we can preview images inside where we uploading it that is in front end 
## Amazing right 👍

```bash
const setFile = (e: React.ChangeEvent<HTMLInputElement>) => {
    const file = e.target.files?.[0];
    if (file) {
      setInput({ ...input, courseThumbnail: file });
      setpreviewFile(file);
      const fileReader = new FileReader();
      fileReader.onloadend = () => {
        if (fileReader.result) {
          setpreviewFile(fileReader.result?.toString());
        }
      };
      fileReader.readAsDataURL(file);
    }
  };
```
