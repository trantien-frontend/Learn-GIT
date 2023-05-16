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

  - Tương tự với những câu git remote, add , origin

  # Clone với https :

  ```bash
    git clone https://github.com/trantien-frontend/Git-Test.git #default
  ```

  - Trường hợp repo mode: private or public nhưng muốn có quyền push code lên remote repo thì phải nhập username và password

  ```bash
    git clone https://username:password@github.com/trantien-frontend/Git-Test.git
    git clone https://trantien-frontend:456789@github.com/trantien-frontend/Git-Test.git #example
  ```

  # Clone voi SSh :

  ```bash
     git@github.com:trantien-frontend/Dizoil-Clone.git
     #Clone bằng host khác
     git@github-thomashenrry97.com:trantien-2/Dizoil-Clone.git
  ```

  # Git Push : git push & git push origin

  ```bash
    git push # auto push to branch main
    git push origin <branch>
  ```

  # Git log : show history push of git

  ```bash
    git log
    git log --oneline
  ```

  # Gil pull

  ```bash
    git pull
  ```

# Read me : usr mark down syntax

[doc md git:](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

[Link tool generate table](https://www.tablesgenerator.com/)

# Git branch

```bash
    git branch #show all branch
    git branch new-branch # create new branch
    git checkout -b new branch # create new branch, jump to new branch
    #same git checkout -b
    git switch -c new branch

    # show all branch remote
    git branch -r
    # show all branch local and remote
    git branch -a

    # update git
    git fetch

    # Rename branch Current
    git branch -m new name branch
    # Rename branch khác với branch current
    git branch -m name-branch-need-to-rename new-name-branch

    # delete branch local
    git branch -D name-branch-need-to-del
    # delete branch origin
    git push origin --delete name-branch-need-to-del

    # create branch on origin form local
    git push -u origin name-branch-need-to-create

    # Khi del branch thủ công trên git, git local nó sẽ chưa cập nhật branch bị xóa
    # dùng git fetch cập nhật lại
    git fetch -p

    # Kiểm tra các branch local được kết nối với origin
    cat .git/config
```

# Git-merge :

- Gộp các commit lại của 2 nhánh với nhau dựa trên thời gian các commit
