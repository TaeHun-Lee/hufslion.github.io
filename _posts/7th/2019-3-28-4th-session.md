---
layout: post
title: 4. 파이썬문법, MTV패턴, 부트스트랩템플릿
category: 7th
---
세션 4 - prod. 김은진


# 4th session 

## Contents
1. Python 문법(2) 
    1. def - 함수
    2. module
    3. class
2. "Hello World!" using MTV pattern
    1. MTV패턴이란?
    2. "Hello World!" 출력하기
3. Customizing for Bootstrap templates
    1. Bootstrap templates 이용법
    2. Customizing 방법
    3. Font Awesome의 icons 이용법

---
***
___


## 1. Python 문법(2)

### 복습
list, for, while, dictionary, tuple 등등

### 1. def - 함수
* 함수란? function : 코드의 묶임에 이름을 붙인 것으로 입력을 받아서 출력을 내보낸다.
* 함수의 정의(선언, 생성) : def 함수명(parameter):

{% highlight html %}
def print_hello():
    print("hello")
{% endhighlight %}

* 함수의 호출

{% highlight html %}
print_hello()
{% endhighlight %}

* 함수를 호출할 때 함수가 명령을 처리하기 위해 필요한 정보를 전달할 수 있는데 이 때, 전달되는 parameters들을 인수(argument)라고 부른다.
* 함수의 수행 결과를 전달받고 싶은 경우 return문 사용한다.*
* 여러 값들을 입력에 전달하고 출력으로 받을 수 있다.

### 2. module
* module이란? 함수, 변수, 클래스들을 모아놓은 파일을 일컫으며, 다른 python 프로그램에서 불러와서 사용할 수 있도록 만들어진 .py 파일이다.
* import를 이용해 module을 불러와 사용할 수 있다.
* 함수뿐만 아니라 변수들도 저장해 불러와 사용 가능하다.

{% highlight html %}
def print_hello():
    print("hello")
{% endhighlight %}

이것을 hello.py라고 저장 후,

{% highlight html %}
import hello
hello.print_hello()
{% endhighlight %}

라고 사용가능하다.

* module.function으로 module 내의 함수를 불러와 이용 가능하다.

### 3. class
* 객체 지향 프로그래밍 (object-oriented programming)
    * 객체(object)
    : 하나의 단위로 묶인 변수(속성, attribute)와 함수들(동작, action)
    * 클래스(class)
    : 객체를 만들기 위한 일종의 틀로 템플릿(template)이라고도 한다.
    * 인스턴스(instance)
    : 클래스(틀)을 이용해 실제로 만들어진 결과물
    
* 클래스와 인스턴스의 생성

{% highlight html %}
class Car:
    color =""
    speed = 0

    def speedUp(self, value):
        self.speed += value
    def speedDown(self, value):
        self.speed -= value

myCar1 = Car()
myCar2 = Car()
myCar1.speedUp(30)
print(myCar1.speed)

{% endhighlight %}

* 클래스 하위의 변수는 attribute, 함수는 method라고 한다.

* 인스턴스 생성 : 클래스명()

* 클래스의 함수(메소드) 호출 : 인스턴스.메소드(parameter) 

* 이 외에도 __init__을 이용한 생성자, 정적 메소드 등이 사용된다.
![class-detail](https://user-images.githubusercontent.com/37901314/54296382-2c5cdc80-45f8-11e9-92d4-e4bf4f414508.PNG)


### Example

* 로또생성 알고리즘을 위한 random모듈과 함수들

{% highlight html %}

#난수생성을 위한 random 모듈 불러오기

import random

#[0,1)(0이상 1미만)의 난수 생성

random.random()

#[1,11)(1이상 11미만)의 리스트 생성(파이썬 내장함수)

list_1_11 = list(range(1,11))
 
#[1,11)(1이상 11미만)의 난수 하나 생성

num = random.randrange(1,11)

#[1,11)(1이상 11미만)의 수 중 홀수 생성

odd = random.randrange(1,11,2)

#순서형 자료(sequence)를 섞어주는 함수

seq = list(range(1,11))

random.shuffle(seq)

#랜덤으로 하나의 원소를 뽑아주는 함수

random.choice(seq)

#랜덤으로 중복 없이 원하는 수의 sample들을 리스트로 뽑아주는 함수

random.sample(seq, 3)

{% endhighlight %}


---
***
___


## 2. "Hello World!" using MTV pattern

### 1. MTV패턴이란?
* : Model, Templates, View를 일컫는 말로 3개의 파일들의 상호교환을 통해 웹이 실행된다.
![mtv](https://user-images.githubusercontent.com/37901314/54296869-0257ea00-45f9-11e9-9079-b4ffde7d0909.PNG)

1. project와 app을 생성한다.
2. settings.py에 app의 생성을 알린다.
3. templates(html)을 생성한다.
4. templates에서 사용될 객체(object)들의 속성(attribute)과 동작(action)을 model.py와 view.py에서 만들어준다.
![mtvd](https://user-images.githubusercontent.com/37901314/54296872-02f08080-45f9-11e9-959d-c8e49cd5e5a2.PNG)
![mtvdd](https://user-images.githubusercontent.com/37901314/54296874-02f08080-45f9-11e9-8482-bc7ce6a8b48a.PNG)

### 2. "Hello World!" 출력하기
* home.html에 print("Hello World!")를 입력해준다.
* view.py에 request가 들어올 시, home.html을 반환해주는 함수를 작성해준다.
* urls.py에 views.py와 home.html을 연결해주는 설정을 해준다.

* 자세한 사항(순서)은 ppt참조
https://github.com/eunjin97/test/files/3026137/0328edit.pdf


---
***
___

## 3. Customizing for Bootstrap templates

### 1. Bootstrap templates 이용법
(이전에 올렸던 내용은 django에서 bootstrap을 이용하는 방법인데, 지금은 거기까지 할 필요가 없어서 html만 수정하는 것으로 바꿨습니다!)
1. https://startbootstrap.com/를 들어가서 원하는 template을 고른 후 다운로드한다.
2. 크롬의 개발자도구(f12)를 이용해 원하는 소스의 위치와 정보, 속성들을 확인한다.
3. index.html로 돌아가 Cntl+F를 이용해 그 곳의 위치를 알아내서 색, 크기, 이미지 등을 원하는대로 수정해준다.


### 3. Font Awesome의 icons 이용법
1. 홈페이지에서 CDN을 긁어와 head에 붙인다.
2. 원하는 아이콘의 html를 복사한다.
3. 원하는 위치에 붙여넣는다.

* 자세한 사항(순서)은 ppt참조
https://github.com/eunjin97/test/files/3026137/0328edit.pdf
