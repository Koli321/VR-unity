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
8) Сделал так, что при столкновении Cube должен менять свой цвет на синий, а при завершении столкновения обратно на красный
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
1) Для начала работы я поменял его состояние из кинематики на использование графитации, а в объекте сфера убрал триггер и сделал те же действия, что и для куба
![image](https://user-images.githubusercontent.com/94520383/192100416-7578407c-0457-4ede-b8f2-171aa39c4b07.png)
![image](https://user-images.githubusercontent.com/94520383/192100524-51275d97-f8cf-4f83-8fb4-f6350aa9f6f0.png)
2) Далее сделал так, чтобы сфера понимала, что падает на куб и меняла цвет
```py
 void Update()
    {

    }

    private void OnCollisionEnter(Collision other)
    {
        other.gameObject.GetComponent<Renderer>().material.SetColor("_Color", Color.blue);
    }

    private void OnCollisionExit(Collision other)
    {
        other.gameObject.GetComponent<Renderer>().material.SetColor("_Color", Color.red);

    }
}
```
3) После я прописал, чтобы пол не меняел цвет, после того как на него падает сфера
```py
  void Update()
    {

    }

    private void OnCollisionEnter(Collision other)
    {
        if (other.gameObject.name == "Cube")
        {
            other.gameObject.GetComponent<Renderer>().material.SetColor("_Color", Color.blue);
        }
    }

    private void OnCollisionExit(Collision other)
    {
        if (other.gameObject.name == "Cube")
        {
            other.gameObject.GetComponent<Renderer>().material.SetColor("_Color", Color.red);
        }

    }
}
```
4) Далее я прописал, чтобы сфера после столкновения пропадала. Для этого я добавил RigidBody Plane и поставил кинематику, чтобы он не упал 
![image](https://user-images.githubusercontent.com/94520383/192101206-e6414f2c-7a31-4416-a491-81e7b438cf35.png)
5) Далее я прописал скрипт, чтобы сфера разрушилась при столкновение с полом
```py
   void Update()
    {
        
    }

    private void OnCollisionEnter(Collision other) {
        if (other.gameObject.name == "Sphere")
        {
            Destroy(other.gameObject);
        }
    }
}
```
## Задание 3
### Реализуйте на сцене генерацию n кубиков. Число n вводится пользователем после старта сцены.
1) Для начала работы я создал объект Point, добавил ему RigidBody и Sphere Collider, чтобы он был одних размером со сферой 
![image](https://user-images.githubusercontent.com/94520383/192101776-66f290d4-be8a-4bad-952b-e1ec34e41a37.png)
2) Далее я создал скрипт, для того чтобы сфера могла разлетаться и проверил это на маленьких сферах
```py
public class PointBoom : MonoBehaviour
{
    // Start is called before the first frame update
    public float radius = 0.5f;

    public float force = 10.0f;

    void Start()
    {
        Vector3 boomPosition = transform.position;
        Collider[] colliders = Physics.OverlapSphere(boomPosition, radius);
        foreach (Collider hit in colliders)
        {
            Rigidbody rb = GetComponent<Rigidbody>();
            if (rb != null)
            {
                rb.AddExplosionForce(force, boomPosition, radius, 3.0f);
            }
        }
    }

    // Update is called once per frame
    void Update()
    {

    }
}
```
![image](https://user-images.githubusercontent.com/94520383/192102623-548221b4-05f6-4ea8-8a02-3d51762a00ab.png)
3) Далее я прописал уже для разрушения большой сферы и добавил Plane уже созданные прифабы Point и SpawnSphere
```py
public class DestroyObject : MonoBehaviour
{
    // Start is called before the first frame update
    public float radius = 0.5f;
    public float force = 10.0f;
    public GameObject prefabBoomPoint;
    public GameObject prefabBoomSphere;
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {

    }

    private void OnCollisionEnter(Collision other)
    {
        if (other.gameObject.name == "Sphere")
        {
            Destroy(other.gameObject);
            Vector3 boomPosition = other.gameObject.transform.position;
            Instantiate(prefabBoomPoint, other.gameObject.transform.position, other.gameObject.transform.rotation);
            Instantiate(prefabBoomSphere, other.gameObject.transform.position, other.gameObject.transform.rotation);
            Collider[] colliders = Physics.OverlapSphere(boomPosition, radius);
            foreach (Collider hit in colliders)
            {
                Rigidbody rb = GetComponent<Rigidbody>();
                if (rb != null)
                {
                    rb.AddExplosionForce(force, boomPosition, radius, 3.0f);
                }
            }
        }
    }
}
```
![image](https://user-images.githubusercontent.com/94520383/192103259-7e4c283b-167a-4462-96a4-aaa15de5d5d3.png)

## Выводы
В данной лабораторной работе, я научился, реализовывать на сцене генерацию n кубиков и ознакомился с основными функциями взаимодействием с объектами внутри редактора.

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
