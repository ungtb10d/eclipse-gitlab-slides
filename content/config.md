## Configure

- One-time configuration of the Git client

  ```
  git config --global user.name "Your Name"
  git config --global user.email you@example.com
  ```

- If you don't use the global flag you can setup a different author for
  each project
- Check settings with
  ```
  git config --global --list
  ``` 
- You might want or be required to use an SSH key.
    - Instructions: http://doc.gitlab.com/ce/ssh/README.html
