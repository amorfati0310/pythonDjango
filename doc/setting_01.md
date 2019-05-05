# Python install
python Mac환경에서 Setting 하기 

iterm +zsh +  hombrew

homebrew가 없다면 설치합시다 

[Homebrew](https://brew.sh/index_ko)


- `brew install python3`
- `brew install pip3`

최신 버전으로 설치가 될 것입니다. 지금 기준으로 python3.7 
3.6(권장) 3.7은 아직 다른 라이브러리들이 충될 되는 경우가 종종 있음

설치하고 python3을 실행시켜 보았습니다.

[](https://www.notion.so/4a131da428954acebef016bc517c9c9a#4ca282dbe9cf48fba2213d66eb42900b)

나가는 것은 ctrl+C → KeyboardInterrupt가 나면 ctrl+D입니다 

pyhon3 

### alias 설정 
    vi ~/.bash_profile
    ```
    alias python="python3"
    alias pip="pip3"
    alias env=". env/bin/activate"
    ```
    
    vi ~/.zsh_profile
    

- editor | Ide 설치

vscode 

[Visual Studio Code - Code Editing. Redefined](https://code.visualstudio.com/)

pycharm community version | pycharm edu version  설치합니다 

[All Developer Tools and Products by JetBrains](https://www.jetbrains.com/products.html?fromMenu)

toolbox로 설치합시다 :) 

toolbox 설치후 pyCharm 

인텔리에서 공짜로 제공하는 툴이니 pyCharm을 써보려 합니다 🤟

### virtualEnv

 개발 환경마다 패키지 버전관리를 해주기 위해 virtualenv를 사용합니다. 

`pip install virtualenv`

이제 작업할 폴더로 가서 example)


### 작업 폴더 만들고 


#### [gitIgnore](https://github.com/github/gitignore/blob/master/Python.gitignore)


#### Django Tutorial Start

* [tutorial-drf](https://www.django-rest-framework.org/tutorial/quickstart/)

튜토리얼 참고 그래도 따라해봅시다.

```
# Create the project directory
mkdir tutorial
cd tutorial
virtualenv -p python3 venv 가상환경 세팅 
source venv/bin/activate 가상환경 액티브 

(venv) 옆에 뜰 겁니다 :) 

Why? 독립적으로 모듈을 관리해주기 위해서
deactivate  (참고) 다시 가상환경 deactive
pip list로 설치한 목록 환인 (참고)



pip install django djangorestframework django-rest-swagger
❯ pip freeze > requirements.txt  

설치후에는 requirement.txt에 써줍니다 :) 
npm에서 package.json -> save 시키는 거라고 보면 이해하기 좋음:)

django-admin startproject drf_tut_01 .
cd drf_tut_01

project structure 

- start project <project folder>
-- __init_py 
-- setting.py 
-- urls.py 
-- wsgi.py
- venv 
- .gitignore
- manage.py
- requirements.txt

django-admin startapp quickstart

아까 구조에 추가적으로 

startapp <project folder>

- migrations 
- __init__py 
- admin.py 
- apps.py 
- models.py 
- test.py 
- views.py 
가 생성됩니다. 

cd ..
sync database 
python manage.py migrate



```

### migrate 

database 변화가 일어날 떄 마다 

`python manage.py migrate` 명령어로 sync를 맞춰줍니다. 
변화된 로그들도 migrations폴더에 쌓이게 됩니다.



### super user 생성 

`python manage.py createsuperuser --email dali@example.com --username dali`


### [Serializers](https://www.django-rest-framework.org/api-guide/serializers/)

* Serializers

복잡한 data (querysets, model instance ) -> JSON | XML 등으로 렌더링할 수 있는 python data 유형으로 변환해줍니다. 

* 1. 복잡 data -> JSON and xml 
* 2. 반대 역할 deserialization validate 수행 후 -> 복잡한 형태로 다시 꽂아줄 수도 있다 :) 


```
from django.contrib.auth.models import User, Group
from rest_framework import serializers


class UserSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = User
        fields = ('url', 'username', 'email', 'groups')


class GroupSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Group
        fields = ('url', 'name')


```



