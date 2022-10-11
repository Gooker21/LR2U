# Анализ данных [в ГеймДеве] в примерах и задачах
Отчет по лабораторной работе #1 выполнил(а):
- Корабельникова Виталия Вадимовича
- НМТ-213929
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | # | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)



Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Задание 1
### Выполнить программу Hello World на Python и Unity
Ход работы:
- Для Python в отчете привести скриншоты с демонстрацией сохранения документа google.colab на свой диск с запуском программы, выводящей сообщение Hello World.
- Для Unity в отчет привести скриншоты выода сообщения Hello World  в консоль.

![image](https://user-images.githubusercontent.com/114081497/192349053-e455efc6-3389-4f29-acc7-7294beddd0c5.png)
![image](https://user-images.githubusercontent.com/114081497/192530935-0c930fae-a65c-43b3-afe5-7e3ededff772.png)




## Задание 2
### В разделе "ход работы " пошагово выполнить каждый пункт с описанием и примером реализации задачи по теме лабораторной работы.



```py

#Import the required modules, numpy for calculation, and Matplotlib for drawing
import numpy as np
import matplotlib.pyplot as plt
#This code is for jupyter Notebook only
%matplotlib inline
# define data, and change list to array
x = [3,21,22,34,54,34,55,67,89,99]
x = np.array(x)
y = [2,22,24,65,79,82,55,130,150,199]
y = np.array(y)
#Show the effect of a scatter plot
plt.scatter(x,y)

def model(a, b, x):
    return a*x + b
    #Tahe most commonly used loss function of linear regression model is the loss function of mean variance difference
def loss_function(a, b, x, y):
    num = len(x)
    prediction=model(a,b,x)
    return (0.5/num) * (np.square(prediction-y)).sum()
#The optimization function mainly USES partial derivatives to update two parameters a and b
def optimize(a,b,x,y):
    num = len(x)
    prediction = model(a,b,x)
    #Update the values of A and B by finding the partial derivatives of the loss function on a and b
    da = (1.0/num) * ((prediction -y)*x).sum()
    db = (1.0/num) * ((prediction -y).sum())
    a = a - Lr*da
    b = b - Lr*db
    return a, b
    #iterated function, return a and b
def iterate(a,b,x,y,times):
    for i in range(times):
        a,b = optimize(a,b,x,y)
    return a,b

#Initialize parameters and display
a = np.random.rand(1)
print(a)
b = np.random.rand(1)
print(b)
Lr = 0.000001
#For the first iteration, the parameter values, losses, and visualization after the iteration are displayed
a,b = iterate(a,b,x,y,1)
prediction=model(a,b,x)
loss = loss_function(a, b, x, y)
print(a,b,loss)
plt.scatter(x,y)
plt.plot(x,prediction)

```
Шаг первый:
![image](https://user-images.githubusercontent.com/114081497/192596934-f38282ba-31c4-4d86-85fa-58e3b7bbcf3b.png)


Шаг Второй:
![image](https://user-images.githubusercontent.com/114081497/192597171-dacd3374-d6c2-4364-a1ca-a3a8b4a4ec03.png)

Шаг третий:
![image](https://user-images.githubusercontent.com/114081497/192597898-9ce06f83-d026-4025-89ec-13b2907109f7.png)

Шаг четвертый:
![image](https://user-images.githubusercontent.com/114081497/192598125-35b4c0c5-03e6-470f-ac84-95345c730357.png)

Шаг пятый:
![image](https://user-images.githubusercontent.com/114081497/192598276-4318d642-549f-4e14-bfad-5e4dfac51a4f.png)
Шаг шестой:
![image](https://user-images.githubusercontent.com/114081497/192598381-6604e2b6-bf7f-48f4-8d1b-55a6c4752b52.png)

## Задание 3
### Какова роль параметра Lr? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ. В качестве эксперимента можете изменить значение параметра.

- Перечисленные в этом туториале действия могут быть выполнены запуском на исполнение скрипт-файла, доступного [в репозитории](https://github.com/Den1sovDm1triy/hfss-scripting/blob/main/ScreatingSphereInAEDT.py).
- Для запуска скрипт-файла откройте Ansys Electronics Desktop. Перейдите во вкладку [Automation] - [Run Script] - [Выберите файл с именем ScreatingSphereInAEDT.py из репозитория].

```py

import ScriptEnv
ScriptEnv.Initialize("Ansoft.ElectronicsDesktop")
oDesktop.RestoreWindow()
oProject = oDesktop.NewProject()
oProject.Rename("C:/Users/denisov.dv/Documents/Ansoft/SphereDIffraction.aedt", True)
oProject.InsertDesign("HFSS", "HFSSDesign1", "HFSS Terminal Network", "")
oDesign = oProject.SetActiveDesign("HFSSDesign1")
oEditor = oDesign.SetActiveEditor("3D Modeler")
oEditor.CreateSphere(
	[
		"NAME:SphereParameters",
		"XCenter:="		, "0mm",
		"YCenter:="		, "0mm",
		"ZCenter:="		, "0mm",
		"Radius:="		, "1.0770329614269mm"
	], 
)

```

## Выводы

Была проделана большая работа по изучению новых языков программирования, лабораторная работа выполнена.

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
