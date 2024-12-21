# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе №4 выполнил(а):
- Степанов Алексей Алексеевич
- РИ-230935
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

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
Познакомиться с одной из первых моделей нейросетей - перцептроном и реализовать эту модель в Unity

## Задание 1. В проекте Unity реализовать перцептрон, который умеет производить вычисления
Ход работы:
- Возьмем скрипт перцептрона
- создадим для него обьект в unity и прикрепим скрипт

![image](https://github.com/user-attachments/assets/861989c7-529c-4914-9da6-ca3db07c5773)

![image](https://github.com/user-attachments/assets/9838a28c-9c45-440d-985b-e81686d3cfff)

Сам скрипт перцептрона:
```C#
public class Perceptron : MonoBehaviour {

  public TrainingSet[] ts;
  double[] weights = {0,0};
  double bias = 0;
  double totalError = 0;

  double DotProductBias(double[] v1, double[] v2) 
  {
    if (v1 == null || v2 == null)
      return -1;
   
    if (v1.Length != v2.Length)
      return -1;
   
    double d = 0;
    for (int x = 0; x < v1.Length; x++)
    {
      d += v1[x] * v2[x];
    }

    d += bias;
   
    return d;
  }

  double CalcOutput(int i)
  {
    double dp = DotProductBias(weights,ts[i].input);
    if(dp > 0) return(1);
    return (0);
  }

  void InitialiseWeights()
  {
    for(int i = 0; i < weights.Length; i++)
    {
      weights[i] = Random.Range(-1.0f,1.0f);
    }
    bias = Random.Range(-1.0f,1.0f);
  }

  void UpdateWeights(int j)
  {
    double error = ts[j].output - CalcOutput(j);
    totalError += Mathf.Abs((float)error);
    for(int i = 0; i < weights.Length; i++)
    {      
      weights[i] = weights[i] + error*ts[j].input[i]; 
    }
    bias += error;
  }

  double CalcOutput(double i1, double i2)
  {
    double[] inp = new double[] {i1, i2};
    double dp = DotProductBias(weights,inp);
    if(dp > 0) return(1);
    return (0);
  }

  void Train(int epochs)
  {
    InitialiseWeights();
    
    for(int e = 0; e < epochs; e++)
    {
      totalError = 0;
      for(int t = 0; t < ts.Length; t++)
      {
        UpdateWeights(t);
        Debug.Log("W1: " + (weights[0]) + " W2: " + (weights[1]) + " B: " + bias);
      }
      Debug.Log("TOTAL ERROR: " + totalError);
    }
  }

  void Start () {
    Train(8);
    Debug.Log("Test 0 0: " + CalcOutput(0,0));
    Debug.Log("Test 0 1: " + CalcOutput(0,1));
    Debug.Log("Test 1 0: " + CalcOutput(1,0));
    Debug.Log("Test 1 1: " + CalcOutput(1,1));    
  }
  
  void Update () {
    
  }
```

- Результат:
![image](https://github.com/user-attachments/assets/db97ae07-7851-4e72-848d-8bd1c1132dee)

  
## Выводы
Я познакомился с первой моделью нейросети - перцептроном и реализовал её работу в Unity
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