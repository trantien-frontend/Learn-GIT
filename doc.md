# git - config : mặc định sử dụng khi không config local, sp nhận diện người push code lên git repository

- global:

  ```bash
   git config --global --list
   git config --global user.name 'name'
   git config --global user.email email
  ```

- local:

```bash
   git config --local --list
   git config --local user.name 'name'
   git config --local user.email email
```

# git status: state file in local

```bash
    git status
```

# git add : add file to staging

```bash
    git add .
    git add namefile
```

# git reset: add file from staging back changes

```bash
    git reset .
    git reset namefile
```

# git commit :

```bash
    git commit -m "messgae"
```

# git push : push file to local

```bash
    git push
```

# ssh-key:

- pass

# ssh-key-agent: chỉ nhập một lần trong phiên làm việc

```bash
    $eval "$(ssh-agent-s)" # turn on ssh agent
    > Agent pid number
    ssh-add ~/.ssh/id_name # name ssh key
    > Could not open a connection to your authentication agent. #agent turning off
    > #agen turning on
```

# Trick dùng nhiều tài khoản git

- tạo ra file config :

  ```txt
  #Default Github
  Host github.com
  User git
  Identity file ~/.ssh/id_rsa

  #Second Github
  Host github.com
  User git
  Identity file ~/.ssh/id_guild
  ```

  ```bash
  git clone git@github.com ... #default git
  git clone git@github--guild.com... #second git
  ```

  - Tương tự với nhũng câu git remote, add , origin
