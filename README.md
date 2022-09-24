# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил(а):
- Максимцов Николай Владимирович
- РИ-300016
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | # | 60 |
| Задание 2 | # | 20 |
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
Основы работы в среде разработки систем
виртуальной и дополненной реальности. Основы работы c Unity.

## Задание 1
### ознакомиться с основными функциями взаимодействием с объектами внутри редактора.
Ход работы:
1) Для начала я создал проект по шаблону 3D - core
2) После чего нужно было создать 3 объекта: Plane, Cube и Shpere
![image](https://user-images.githubusercontent.com/94520383/191991603-c7d730bb-86ef-43c1-9974-2e3c16430b0c.png)
3) Затем установил компонент Sphere Collider для объекта Sphera
![image](https://user-images.githubusercontent.com/94520383/191991981-f68b59d7-2f30-4e13-a219-c5be8be39b38.pn
4) И затем настроил его как триггер как показано в скриншоте до этого 
5) После я перекрасил объект куб в красный цвет
![image](https://user-images.githubusercontent.com/94520383/191992226-62503bb6-995b-4ce4-aba8-95b1c786e9c3.png)
6) Добавил кубу симуляцию физики, при это куб не должен проваливаться под Plane
![image](https://user-images.githubusercontent.com/94520383/191992382-449c5e5e-7640-458f-bc4f-4634cadb4ef5.png)
7) После этого я, написал скрипт, который будет выводить в консоль сообщение о том, что объект Sphere столкнулся с объектом Cube
```py
void Update()
    {

    }

    private void OnTriggerEnter(Collider other)
    {
        Debug.Log("Произошло столкновение с " + other.gameObject.name);
    }

    private void OnTriggerExit(Collider other)
    {
        Debug.Log("Завершенно столкновение с " + other.gameObject.name);
    }
}

```
8) Сделал так, что при столкновении Cube должен менять свой цвет на зелёный, а при завершении столкновения обратно на красный
```py
void Update()
    {

    }

    private void OnTriggerEnter(Collider other)
    {
        Debug.Log("Произошло столкновение с " + other.gameObject.name);
        other.GetComponent<Renderer>().material.SetColor("_Color", Color.blue);
    }

    private void OnTriggerExit(Collider other)
    {
        Debug.Log("Завершенно столкновение с " + other.gameObject.name);
        other.GetComponent<Renderer>().material.SetColor("_Color", Color.red);
    }
}

```
- Определите связанные функции. Функция модели: определяет модель линейной регрессии wx+b. Функция потерь: функция потерь среднеквадратичной ошибки. Функция оптимизации: метод градиентного спуска для нахождения частных производных w и b.


## Задание 2
### Что произойдёт с координатами объекта, если он перестанет быть дочерним?
### Создайте три различных примера работы компонента RigidBody?
Ход работы: 

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
![Максимцов](https://user-images.githubusercontent.com/94520383/191990540-cbeb500a-d545-4d59-bac7-ec9f4de3e5a9.jpg)

```

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

Абзац умных слов о том, что было сделано и что было узнано.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
