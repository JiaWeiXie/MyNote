# 我的筆記

### Atom

> Markdown Preview 快捷鍵

- Ctrl+Shift+M

> Atom自動排版插件

1. 安裝Ruby
2. 安裝Ruby Package Manager  'gem'
3. 安裝rubocop
  ``
    $ gem install rubocop
  ``  
4. 安裝Atom atom-beautify
  ``
  $ apm install atom-beautify
  ``
5. Atom => Setting => Packages => atom-beautify
   </br>Default Beautifier是Rubocop，如果想要在存檔的時候自動作beautify，就把Beautify On Save打鉤。Indent size記得設成2
6. USE快捷鍵:
  ``
  Ctrl+Alt+B
  ``

> Themes

UI Theme: </br>
*  Atom Material

Syntax Theme: </br>
*  Material

### PostgreSQL

> Install DataBase(macOS):

1.Update Homebrew
```
$ brew update
$ brew doctor
```

2.Install Postgres
```
$ brew install postgresql
```

3.Create/Upgrade a default database
```
$ initdb /usr/local/var/postgres -E utf8
```

4.Install Lunchy
```
$ gem install lunchy
```

5.Start/Stop Postgres
  </br>
*  <font color=#0099ff size=3>9.6.1(Postgre version)</font>
* Default User Is Systom User Name

```
$ mkdir -p ~/Library/LaunchAgents
$ cp /usr/local/Cellar/postgresql/9.6.1/homebrew.mxcl.postgresql.plist ~/Library/LaunchAgents/

$ launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist

Start Database:
$ lunchy start postgres

Stop DataBase:
$ lunchy stop postgres
```

7.Install GUI manage tool
* pgAdmin

###  MySQL

> Install MySQL and use

1.Update Homebrew
```
$ brew update
$ brew doctor
```

2.Install
```
$ brew install mysql
```

3.setup macOS
```
$ unset TMPDIR
$ mkdir /usr/local/var
$ mysql_install_db --verbose --user=`whoami` --basedir="$(brew --prefix mysql)" --datadir=/usr/local/var/mysql --tmpdir=/tmp
```
