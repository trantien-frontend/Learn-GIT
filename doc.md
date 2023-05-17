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
  NOTE: Khi merge sai branch

```bash
  git log # lấy ra mã hash của merge sai
  git revert -m 1 hashCode # undo

  git reset --hard <commit trước commit merge>

# Conflict Khi Merger Branch

- Tìm file bị conflict trong tab source và fix
- add . or add file
- câu lệnh thêm commit cho file vừa fix :

  - git merge --continue --no-edit
  - git merge --continue
  - git commit -m 'message'

- git push
```

### Note : Git Pull là sự kết hợp giữa ** git pull ** or và ** git merge ** : lấy dữ liệu mới nhất từ origin về

# git -rebase

```bash
  git rebase
  git push -f
```

NOTE : rebase nhánh feature/login vào main : base lịch sử commit của main nó bị đè bởi feature login

ưu điểm :

- Tạo một commit sạch sẽ, dễ nhìn
- Nếu làm cá nhân thì phù hợp

<<<<<<< Updated upstream

# git checkout, git restore : undo local change về trạng thái ban đầu

=======

# git checkout, git restore : undo change

> > > > > > > Stashed changes

```bash
   git checkout name-file
   git restore name-file
```

UI VSCODE : discard change

<<<<<<< Updated upstream

# git Staged change : undo staged change về trạng thái ban đầu

=======

# git Staged change : undo staged change về change

> > > > > > > Stashed changes

```bash
    git reset
```

<<<<<<< Updated upstream

# Hoàn tác những file commited về trạng thái ban đầu :

=======

# Hoàn tác những file commited về change :

> > > > > > > Stashed changes

```bash
  git restore --sourc=hashcode namefile
```

# Hoàn tác về commited mà mình mong muốn theo hash-code :

```bash
  git reset hash-code # default : --mixed --> hoàn tác change

  git reset --soft hash-code # hoàn tác về stage change

  git reset --hard hash-code # xóa luôn thay đổi

  git reset --merge hash-code # giống hard, không mất code
```

- Khi reset tại local thì trên origin vẫn còn, khi push lên lại thì origin nó sẽ mất commit thì nó không cho phép nên phải sài :

```bash
  git push -f
```

# git revert : tạo ra một commit trái ngược với commit hiện tại

```bash
  git revert hash-code --no-edit # AUTO ADD COMMIT MESSAGE
  git revert hash-code  # cho edit lại cái mesage commit
```

- đối với những merge commit không thể revert thông thường phải revert từ parent node
  note: Khi merge từ branch B vào branch A, thì parent đầu tiên luôn là branch A

```bash
  git revert -m 1 hash-code --no-edit
  git revert -m 1 hash-code
  # -m 1 : revert Branch B từ Branch A
```
