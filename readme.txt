■ Install
  - Django
　  https://docs.djangoproject.com/ja/3.0/topics/install/#installing-official-release
  - Python  
    https://www.python.org/downloads/release/python-373/

1) python 3.7.3
   - Windows x86-64 executable installer
     ■ Add Python 3.7 to PATH

2) Command prompt
   python -VER

3) Python の仮想環境
   python -m venv venv_private_diary

4) Python の仮想環境に入る/でる
   cd venv_private_diary\Scripts
   activate.bat
   deactivate

5) Djangoインストール(仮想環境)
   activate.bat
   (venv_private_diary) pip install django==2.2.2
   
6) PyCharmインストール(仮想環境)
   - download pycharm-community
   https://www.jetbrains.com/ja-jp/pycharm/download/
    
7) PostgreSQLインストール(仮想環境)
   v 10.12
   https://www.enterprisedb.com/downloads/postgres-postgresql-downloads

8) PostgreSQL環境変数設定
   - システム環境変数設定

9) データベース作成(仮想環境)
   (venv_private_diary) psql -U postgres
   
   (postgres=#) create database private_diary;
   
   データベース一覧: (postgres=#) \l
   ログアウト: (postgres=#) \q

10) psycopg2 PostgreSQL接続ドライバインストール(仮想環境)
    (venv_private_diary) pip install psycopg2-binary

11) Djangoプロジェクト作成 (仮想環境)
    (venv_private_diary) django-admin startproject private_diary

12) Djangoアプリケーション作成 (仮想環境)
    cd django_private
　　(venv_private_diary) python manage.py startapp diary

13) PyCharmからプロジェクトフォルダ（private_diary）を開く

14) Djangoプロジェクトの仮想環境で使用するPythonを設定する。
　　PyCharm [File]- [settings] [Project Interpreter]
      [venv_private_diary\Scripts\python.exe]

-------------------------------------------------------------
01) マイグレーション (仮想環境)
    新しく作成・変更したモデルをデータベースに反映する。
    cd django_private
　　(venv_private_diary) python manage.py makemigrations
　　(venv_private_diary) python manage.py migrate

02) マイグレーションファイル作成コマンド (makemigrations)
　　1) [PyCharm] [Run] [Edit Configurations]
　　2) [Copy Configurations]から[runserver]をコピーし、
       [Name], [Parameters]を makemigrationsに変更する。
　　3) makemigrations [▷]ボタンより実行する。
    --- 成功の場合 ---
    Migrations for 'accounts':
    accounts\migrations\0001_initial.py
    - Create model CustomUser

03) django-allauthのインストール (仮想環境)
    Djangoのローカル認証・ソーシャル認証をサポートするパッケージ
    
　　(venv_private_diary) pip install django-allauth

04) スーパーユーザーの作成 (仮想環境)
    
　　(venv_private_diary) python manage.py createsuperuser --settings private_diary.settings_dev
    ※ no password supplied エラーの場合
　　set DB_USER=postgresユーザー名
　　set DB_PASSWORD=postgresパスワード

　　user= admin
    mail address=admin@example.com
    password=********
　　　
05) データベース操作モード (仮想環境)
　　(venv_private_diary) python manage.py dbshell --settings private_diary.settings_dev
    
    テーブル一覧の表示
    private_diary=# \dt

    テーブル全レコードの表示
    private_diary=# select * from diary_diary;

10) テストモジュールの作成/ テスト実行
　　・[diary] - tests.py 削除
　　・[diary] - tests python package 作成
　　・[diary] - [tests] - test_views.py 作成
　　Pycharm
    ・[Run]コマンド - [test]
    Command Prompt
    (venv_private_diary) python manage.py test --settings private_diary.settings_dev

11) DBバックアップコマンド(独自コマンド)
    (venv_private_diary) python manage.py backup_diary --settings private_diary.settings_dev


