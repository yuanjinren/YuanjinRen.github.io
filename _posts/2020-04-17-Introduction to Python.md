---
layout: post
title: Introduction to Python
---
************************************************************
************************************************************
```python
print('Hello World!')
```

    Hello World!



```python
name = input('What is your name?')
```

    What is your name?Yuanjin Ren



```python
print('Hello ', end='')
print(name)
```

    Hello Yuanjin Ren



```python
print('Hello ')
print(name)
```

    Hello 
    Yuanjin Ren



```python
#String
a = 'apples'
```


```python
type(a)
```




    str




```python
#integer
b = 4
type(b)
```




    int




```python
#float
f = 4.1111
type(f)
```




    float




```python
#Boolean
d = True
type(d)
```




    bool




```python
a + b
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-11-bd58363a63fc> in <module>
    ----> 1 a + b
    

    TypeError: can only concatenate str (not "int") to str



```python
a + str(b)
```




    'apples4'



Python does not require explictly declare variable types, unlike Java or other languages.


```python
b / f
```




    0.9729756026367637




```python
14 / b
```




    3.5




```python
a = "Hello"
b = "World"
print(a+b)
```

    HelloWorld



```python
print(a[0])
```

    H



```python
# -1 starting from the end
print(a[-1])
```

    o



```python
print('World'[0:4])
```

    Worl



```python
print(b[::-1])
```

    dlroW


Popular String Functions


```python
a = "Hello World"
print('-'.join(a))
```

    H-e-l-l-o- -W-o-r-l-d



```python
print(a.startswith('Wo'))
```

    False



```python
print(a.endswith('rld'))
```

    True



```python
print(a.replace('o','0').replace('d','[)').replace('l','1'))
```

    He110 W0r1[)



```python
print(a.split())
```

    ['Hello', 'World']



```python
print(a.split('o'))
```

    ['Hell', ' W', 'rld']



```python
a[0] = b
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-27-9bd2a5b7e829> in <module>
    ----> 1 a[0] = b
    

    TypeError: 'str' object does not support item assignment


String is an immutable data type. Once you instantiate a string, you cannot change any character in its set. 


```python
for i in range(5):
    print('Hi!\n')
```

    Hi!
    
    Hi!
    
    Hi!
    
    Hi!
    
    Hi!
    



```python
for i in range(3):
    for j in range(3):
        print(i,j)
    print('This statment is within the i-loop, but not the j-loop. ')    
```

    0 0
    0 1
    0 2
    This statment is within the i-loop, but not the j-loop. 
    1 0
    1 1
    1 2
    This statment is within the i-loop, but not the j-loop. 
    2 0
    2 1
    2 2
    This statment is within the i-loop, but not the j-loop. 



```python
for i in range(3):
    for j in range(3):
        print(i,j)
        print('This statment is within the i-loop, but not the j-loop. ')   
```

    0 0
    This statment is within the i-loop, but not the j-loop. 
    0 1
    This statment is within the i-loop, but not the j-loop. 
    0 2
    This statment is within the i-loop, but not the j-loop. 
    1 0
    This statment is within the i-loop, but not the j-loop. 
    1 1
    This statment is within the i-loop, but not the j-loop. 
    1 2
    This statment is within the i-loop, but not the j-loop. 
    2 0
    This statment is within the i-loop, but not the j-loop. 
    2 1
    This statment is within the i-loop, but not the j-loop. 
    2 2
    This statment is within the i-loop, but not the j-loop. 



```python
groceries = []
```


```python
groceries.append('orange')
groceries.append('meat')
groceries.append('apples')

```


```python
print(groceries)
```

    ['orange', 'meat', 'apples']



```python
print(groceries[1])
```

    meat



```python
len(groceries)
```




    3




```python
groceries.sort()
```


```python
print(groceries)
```

    ['apples', 'meat', 'orange']



```python
veggie = [x for x in groceries if x is not 'meat']
veggie
```




    ['apples', 'orange']




```python
groceries.remove('apples')
groceries
```




    ['meat', 'orange']




```python
groceries[0] = 2
groceries
```




    [2, 'orange']




```python
groceries.sort()
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-45-dba2eaa75c63> in <module>
    ----> 1 groceries.sort()
    

    TypeError: '<' not supported between instances of 'str' and 'int'



```python
L = ['x',1,3,'y']
print(L.pop())
```

    y


Lists are objects


```python
L = [2, 5, 1, 4]
X = L
```


```python
L.sort()
```


```python
print(X)
```

    [1, 2, 4, 5]



```python
L.append(3)
print(X)
```

    [1, 2, 4, 5, 3]



```python
print(L[1:-1])
```

    [2, 4, 5]



```python
print(L[2:])
```

    [4, 5, 3]



```python
print(L[:-2])
```

    [1, 2, 4]



```python
print(L[1:-1:2])  #2 is the gap
```

    [2, 5]



```python
L
```




    [1, 2, 4, 5, 3]



Mathmatical functions: L1 = x^2, for x in (0,...,9)


```python
L1 = [x**2 for x in range (10)] # range(n): returns an interator from 0 to n-1
```


```python
print(L1)
```

    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]



```python
L2 = [2**i for i in range(4)]
```


```python
print(L2)
```

    [1, 2, 4, 8]



```python
words = 'The quick brown fox jumps over the lazy dog'.split()
```


```python
print(words)
```

    ['The', 'quick', 'brown', 'fox', 'jumps', 'over', 'the', 'lazy', 'dog']



```python
upper = [w.upper() for w in words]
```


```python
upper
```




    ['THE', 'QUICK', 'BROWN', 'FOX', 'JUMPS', 'OVER', 'THE', 'LAZY', 'DOG']




```python
stuff = [[w.upper(),w.lower(),len(w)] for w in words]
```


```python
stuff
```




    [['THE', 'the', 3],
     ['QUICK', 'quick', 5],
     ['BROWN', 'brown', 5],
     ['FOX', 'fox', 3],
     ['JUMPS', 'jumps', 5],
     ['OVER', 'over', 4],
     ['THE', 'the', 3],
     ['LAZY', 'lazy', 4],
     ['DOG', 'dog', 3]]




```python
s = input('Give numbers separated by comma:')
```

    Give numbers separated by comma:2,10,11,111



```python
x = [int(n) for n in s.split(',')]
```


```python
print(x)
```

    [2, 10, 11, 111]



```python
y = s.split(',')
```


```python
print(y)
```

    ['2', '10', '11', '111']



```python
print(y[0]+y[0])
```

    22



```python
groceries = ('oranges', 'meat', 'apples', 2.5, True)
```


```python
groceries[2]
```




    'apples'




```python
L = [1, 2, 3]
```

sets




```python
numbers = range(10)
```


```python
evens = [2,4,6,8]
```


```python
evens = set(evens)
```


```python
numbers = set(numbers)
```


```python
odds = numbers - evens
```


```python
print(odds)
```

    {0, 1, 3, 5, 7, 9}



```python
a = [2,1,2,1]
print(a)
```

    [2, 1, 2, 1]



```python
a = set(a)
```


```python
print(a)
```

    {1, 2}


Dictionary: a map of keys to the values, keys must be unique, and immutable


```python
simple_dic = {'csci415635' : 'Data Mining'}
```


```python
print(simple_dic['csci415635'])
```

    Data Mining



```python
classes = {'csci415635' : 'Data Mining',
           'csci7755': 'big data'}
```


```python
print('csci7755' in classes)
```

    True



```python
classes['L14'] = 'social networks'
```


```python
print(classes['L14'])
```

    social networks



```python
print(classes.keys())
```

    dict_keys(['csci415635', 'csci7755', 'L14'])



```python
print(classes.values())
```

    dict_values(['Data Mining', 'big data', 'social networks'])



```python
classes['L14'] = 'gradual social networks'
```


```python
print(classes['L14'])
```

    gradual social networks


For searching operations, prefer dictionary and sets


```python
import random

```


```python
L = [random.choice(range(10000000)) for i in range(10000)]
L
```




    [5892928,
     2593411,
     7502833,
     3789553,
     7723815,
     343971,
     4244332,
     4191248,
     2603580,
     9591965,
     4298659,
     4437136,
     5751768,
     1903308,
     1954057,
     6085563,
     1327824,
     7764105,
     9800187,
     3810104,
     3817739,
     2884175,
     5177059,
     257177,
     1594470,
     3269513,
     6122344,
     4493635,
     9492660,
     2875411,
     677987,
     4658711,
     3868969,
     5338666,
     3873178,
     6386074,
     9181229,
     3627096,
     82248,
     1265088,
     1772503,
     8553003,
     2830138,
     6617215,
     1373493,
     6371358,
     8470523,
     3537614,
     4239094,
     7096773,
     7533999,
     6860419,
     3091220,
     6128685,
     2710897,
     5375814,
     2735278,
     6293709,
     7729201,
     1249700,
     5326640,
     804739,
     6554564,
     3654433,
     948590,
     5860974,
     7231131,
     1126098,
     2620463,
     2843011,
     4182583,
     9157281,
     9593820,
     7564685,
     620025,
     1301157,
     332372,
     7694615,
     6692737,
     3138230,
     2142270,
     7418499,
     9392112,
     3476299,
     9472225,
     4145207,
     1664020,
     8474579,
     2478285,
     8904658,
     9995247,
     8887973,
     3756017,
     9099760,
     4556842,
     3751359,
     6564629,
     833454,
     534501,
     2806604,
     2149973,
     638768,
     1085073,
     7968966,
     8467543,
     3560665,
     4306099,
     4256231,
     5028969,
     2849153,
     1468413,
     8783107,
     5720906,
     457489,
     6908187,
     7609236,
     5163800,
     4676672,
     1132476,
     3020078,
     7146269,
     1318921,
     1113014,
     4888775,
     4798620,
     2536560,
     2136259,
     7598157,
     8832862,
     4108967,
     3204187,
     95484,
     2112870,
     4900495,
     2935430,
     1158700,
     4300088,
     6830903,
     9211165,
     9481517,
     5527475,
     8721005,
     425111,
     4118906,
     3853236,
     7452543,
     2279526,
     3560866,
     2483945,
     6944148,
     2356703,
     2881398,
     2540276,
     9013372,
     6777253,
     9089419,
     5682701,
     8098109,
     9171551,
     5903707,
     4187994,
     4637294,
     1213506,
     7071721,
     3640366,
     8123262,
     4267617,
     6174400,
     8318249,
     6949041,
     1451841,
     4576224,
     891159,
     4221744,
     7222017,
     5593331,
     3559710,
     2256763,
     4304415,
     2232309,
     4979803,
     3276079,
     4276152,
     5943653,
     5281304,
     4383973,
     4745363,
     420852,
     8654429,
     5448134,
     8320980,
     2162611,
     7943838,
     9579558,
     2490817,
     3720421,
     2805169,
     9626892,
     837957,
     1354209,
     6744306,
     9320848,
     6446771,
     4013235,
     2674171,
     594198,
     1288082,
     5210206,
     778471,
     4891020,
     8503353,
     2542145,
     7370896,
     8453842,
     4856205,
     9502636,
     3641800,
     7670632,
     1242465,
     1670004,
     6242755,
     8700586,
     1222449,
     9352441,
     4465197,
     3869456,
     8718285,
     4724529,
     9572095,
     1738998,
     6318139,
     9534471,
     9511809,
     577009,
     1966996,
     2080126,
     5247599,
     8040217,
     9244042,
     3822699,
     8772670,
     5206860,
     4402819,
     5330666,
     8643507,
     1304639,
     6302032,
     1784500,
     9970869,
     62252,
     2303645,
     7042491,
     1956723,
     2876368,
     4562531,
     3070899,
     9235919,
     8605399,
     1729765,
     1468338,
     7300440,
     5839923,
     3014653,
     6933267,
     3878889,
     3254016,
     1400594,
     4875494,
     8724705,
     6597681,
     9647298,
     2030195,
     5936427,
     5048760,
     5561121,
     6424465,
     3228542,
     7973748,
     9153073,
     606033,
     5934507,
     8961806,
     2532862,
     1045245,
     4427112,
     2156682,
     2339320,
     3160712,
     1580521,
     7347517,
     6717932,
     1364105,
     9105238,
     2270762,
     84838,
     106541,
     8138069,
     7993283,
     2740062,
     2318352,
     7924910,
     35977,
     4507653,
     2569464,
     5712468,
     7159085,
     628929,
     8908013,
     2853290,
     2544436,
     5197197,
     6481683,
     1743961,
     4085920,
     4628926,
     5997685,
     8037513,
     2629987,
     1366243,
     1098811,
     4046774,
     6351824,
     5941115,
     9565385,
     4825242,
     1908317,
     2458495,
     6346523,
     5643739,
     6870801,
     9753782,
     1466060,
     1107761,
     6015832,
     2626269,
     1089317,
     1479831,
     1763526,
     707249,
     7124072,
     2853120,
     5637273,
     8788095,
     7044339,
     7224343,
     9864577,
     8911155,
     5974000,
     270771,
     4960487,
     5964393,
     6088168,
     4471526,
     634164,
     3416790,
     1132141,
     6099994,
     3362808,
     4525353,
     3145363,
     5122264,
     5925077,
     6169619,
     4017519,
     5864470,
     3924066,
     4744738,
     3646395,
     6780706,
     1982006,
     5296320,
     1587214,
     7693224,
     8976002,
     7318961,
     659018,
     5021166,
     1911263,
     1524952,
     7542983,
     5034948,
     8015282,
     5814104,
     6084903,
     5416801,
     7286496,
     4294530,
     403840,
     5371711,
     2259159,
     5351160,
     798188,
     7195622,
     6713580,
     2023740,
     2922807,
     290225,
     3583833,
     859235,
     9983039,
     5093680,
     7171430,
     4024163,
     6470282,
     8470315,
     5980715,
     1719472,
     7137640,
     6359021,
     3729893,
     6464674,
     1944761,
     3951382,
     4722647,
     6083807,
     3954224,
     7826200,
     6839355,
     9679616,
     7987812,
     2084055,
     2618201,
     9489968,
     6598859,
     7351440,
     1694865,
     2654877,
     45937,
     8139389,
     6809459,
     7223111,
     4305714,
     5671512,
     3973781,
     9120431,
     7929135,
     7654509,
     5995866,
     3157970,
     7499,
     3935006,
     890882,
     7254238,
     2167349,
     9642525,
     7028803,
     6900919,
     7713516,
     7135995,
     1414961,
     4488474,
     395100,
     4756405,
     2066598,
     198329,
     9837586,
     6077211,
     2022955,
     3419429,
     3066213,
     9109800,
     614149,
     8594427,
     2124793,
     2410756,
     5652239,
     4135450,
     847202,
     6175007,
     7808444,
     7212345,
     2343381,
     9658721,
     2220621,
     3855896,
     1226618,
     7056515,
     8725819,
     1557546,
     7697363,
     8110630,
     2995920,
     1608779,
     2967666,
     3194492,
     7144031,
     9749148,
     5779693,
     5912428,
     8453068,
     6248284,
     4810290,
     8267262,
     5728056,
     9279567,
     8696839,
     1184609,
     1033928,
     4112954,
     2212405,
     7290666,
     9536665,
     5014317,
     4828494,
     5597817,
     8834433,
     9754879,
     397648,
     6926991,
     96758,
     2669028,
     6940009,
     7537058,
     856791,
     5636107,
     7686289,
     5878188,
     179746,
     2344040,
     3548778,
     7982924,
     9481963,
     6551648,
     9277426,
     4013780,
     7865629,
     1710239,
     1641923,
     1808375,
     5613855,
     9047872,
     4643774,
     5851815,
     2351720,
     3031483,
     6652848,
     5954927,
     1016294,
     244073,
     9623044,
     1260388,
     1211431,
     4558543,
     8319063,
     9337766,
     4376351,
     2635884,
     8606100,
     8100371,
     9690538,
     3555482,
     9859099,
     5600673,
     8068783,
     661109,
     569572,
     8056685,
     1558395,
     163422,
     864017,
     2444719,
     2836520,
     3407617,
     237001,
     689508,
     6729649,
     3668019,
     1244160,
     5883422,
     5843515,
     7001501,
     1029838,
     5165979,
     7743515,
     2712263,
     3094623,
     8597,
     5519378,
     1057612,
     2433073,
     857682,
     569648,
     669318,
     4478221,
     5968263,
     7064743,
     5149537,
     3446910,
     3254458,
     433570,
     6676947,
     328982,
     4659888,
     9603834,
     8146697,
     8969259,
     8576476,
     6942071,
     6958961,
     985842,
     4830608,
     6101286,
     10814,
     806233,
     6298001,
     6513685,
     2284415,
     8705243,
     7212279,
     7703463,
     5944837,
     1525688,
     8685934,
     5488043,
     3904240,
     5054289,
     1585161,
     464514,
     5065444,
     5262016,
     2318959,
     7812757,
     6897738,
     6466676,
     9705768,
     7083410,
     6939657,
     6683484,
     7150931,
     2430096,
     249838,
     9098097,
     2353702,
     1604402,
     6720418,
     6481348,
     194236,
     9062162,
     9941860,
     5213890,
     4462441,
     9619511,
     9019329,
     4455977,
     8997431,
     2925348,
     9195244,
     5540624,
     1661075,
     5749794,
     914880,
     9159732,
     3462968,
     1580627,
     2182274,
     7387420,
     2734253,
     8529995,
     8295205,
     1840373,
     8840659,
     8247923,
     8195092,
     606947,
     3673542,
     6760001,
     9801131,
     8058174,
     6597322,
     6168493,
     1811322,
     5156291,
     5357721,
     2041945,
     9488209,
     8996851,
     3067592,
     964684,
     8817319,
     8230844,
     9883755,
     5147184,
     4044850,
     1250630,
     597745,
     8759150,
     4340066,
     8077129,
     4015549,
     68409,
     4021763,
     3843534,
     6057904,
     2343402,
     5789284,
     8550183,
     6377087,
     1940804,
     6117013,
     3106968,
     2162061,
     9903126,
     3476917,
     8228673,
     6013034,
     3086567,
     9732618,
     7776690,
     2072037,
     9552591,
     6955278,
     9842833,
     8792944,
     2408632,
     1048613,
     8406165,
     3334332,
     7396122,
     7078050,
     1199816,
     2771369,
     5224280,
     7120888,
     2864244,
     4198070,
     8042963,
     2136694,
     4002174,
     560017,
     5509155,
     5402231,
     569476,
     2396480,
     5933002,
     1453344,
     9154377,
     55678,
     3227245,
     7998662,
     5321780,
     3873723,
     5445509,
     3434983,
     984223,
     7145684,
     2988042,
     5928756,
     175204,
     8548819,
     6118997,
     8202869,
     977005,
     8979939,
     6158703,
     3361854,
     8029483,
     2778308,
     4188175,
     7437332,
     6396203,
     4900136,
     9094619,
     3189774,
     9772313,
     2096378,
     9693210,
     3379776,
     5298811,
     9526220,
     9379469,
     2820851,
     9454911,
     498716,
     6650015,
     1910777,
     1108764,
     2143237,
     2710869,
     7087105,
     9772104,
     3490941,
     5563791,
     3129419,
     8053590,
     6905151,
     2659441,
     3915943,
     3767955,
     4848292,
     5806477,
     4697749,
     4427373,
     2916822,
     1655267,
     5168278,
     383378,
     1287068,
     7446325,
     1048335,
     9033521,
     7143029,
     5061520,
     3771214,
     7856700,
     877264,
     5085554,
     2883525,
     9407894,
     9496456,
     7968950,
     3895388,
     3787533,
     5254034,
     5913263,
     1454518,
     1265669,
     4422722,
     9513605,
     1347328,
     4060214,
     3076739,
     1957502,
     5827995,
     1782486,
     1688327,
     2561169,
     907452,
     9137561,
     1525028,
     7609056,
     6457471,
     1721317,
     7728234,
     198945,
     4136987,
     3571672,
     8137545,
     3082411,
     6214479,
     2911845,
     585342,
     6098244,
     6609566,
     5463826,
     4296194,
     4184499,
     9279427,
     5978565,
     5215705,
     8152316,
     5217389,
     911832,
     3350932,
     1192612,
     5358305,
     9918073,
     435906,
     2540238,
     8865589,
     6828450,
     323919,
     2332160,
     15771,
     2602077,
     6837330,
     6168379,
     9279972,
     4659770,
     7309416,
     6355646,
     2684566,
     6895207,
     3415574,
     5488447,
     2774588,
     465723,
     1788189,
     2530616,
     507570,
     5034164,
     7902587,
     3271632,
     8747540,
     1253665,
     36705,
     9727986,
     7178294,
     6455305,
     9198297,
     7353199,
     8504407,
     7917566,
     7490016,
     1859442,
     4224253,
     7066250,
     8862545,
     9517213,
     6978615,
     2319489,
     6510641,
     1078947,
     7982765,
     9641703,
     2744599,
     9111363,
     6248211,
     7646007,
     584424,
     3970751,
     3143586,
     5928275,
     4747502,
     7550317,
     6280875,
     6253647,
     6269533,
     5158059,
     3095817,
     5870338,
     2196972,
     689279,
     9845048,
     2133912,
     5500029,
     5095419,
     7095721,
     2954797,
     4929737,
     5104404,
     5044371,
     9066913,
     4370970,
     2533727,
     4809234,
     2779629,
     9621412,
     3057871,
     4467071,
     6934563,
     3494314,
     9997608,
     419839,
     631928,
     4239142,
     8371877,
     4316490,
     8378542,
     4095571,
     4585751,
     7472501,
     4561807,
     5715657,
     6340291,
     2508227,
     6814347,
     5330827,
     9346892,
     1438874,
     854230,
     3215621,
     629607,
     3627591,
     8386713,
     6573442,
     9922237,
     4841778,
     4556862,
     5222869,
     9204555,
     2929973,
     3716054,
     4876468,
     8215288,
     1984151,
     585984,
     6067092,
     974193,
     782369,
     1092136,
     8423104,
     2838214,
     2686026,
     445075,
     5067682,
     6239624,
     7330358,
     7352192,
     6401150,
     3945600,
     7165020,
     5212314,
     8027999,
     5553732,
     6723631,
     1063594,
     5283101,
     3866210,
     5189901,
     2562616,
     ...]




```python
import time
t = time.process_time()
count = 0
for x in range(1000):
    if x in L:
        count +=1
print(time.process_time()-t)
```

    0.2751220000000001



```python
S = set(L)
t = time.process_time()
count = 0
for x in range(1000):
    if x in L:
        count +=1
print(time.process_time()-t)
```

    0.23667399999999983



```python
#Write to a file
with open('datamiming1.txt','w') as f:
    f.write('Hello World! \n')
    f.write('Everyone is Happy!\n')
```


```python
#Write to a file
f = open('datamining2.txt','w')
f.write('Hello World! \n')
f.write('Everyone is Happy!\n')
f.close()
```


```python
#Reading from a file
with open('datamiming1.txt','r') as f:
    data = f.readlines()
    for line in data:
        words = line.split()
        print(words)
```

    ['Hello', 'World!']
    ['Everyone', 'is', 'Happy!']



```python
#Reading from a file
f = open('datamining2.txt','r')
#count the lines and words in a file
lines = 0
words = 0
for line in f:
    lines +=1
    words += len(line.split())
    
print("There are %i lines and %i words in the %s file," %(lines,words,'datamining2.txt'))
```

    There are 2 lines and 5 words in the datamining2.txt file,


Functions:
def, lambda


```python
def linear(x):
    a = 2
    b = 1
    return a*x+b
```


```python
print(linear(10))
```

    21



```python
def displayPerson(name, age, univ = 'New York Tech'):
    print("My name is " + name + ", I am " + age + " years old and I study at " + univ + ".")
```


```python
displayPerson('Tina','25')
```

    My name is Tina, I am 25 years old and I study at New York Tech.



```python
displayPerson('Mike','22','Florida')
```

    My name is Mike, I am 22 years old and I study at Florida.



```python
#lambda, A lambda function does not need to be assigned to variable
f = lambda x, y: x+y


```


```python
print(f(2,3))
```

    5



```python
#Map Function: list of inputs, list of outputs
def dollar2euro(x):
    return 0.89*x
def euro2dollar(x):
    return 1.12*x
```


```python
amounts = (100,200,300,400)
dollars = map(euro2dollar, amounts)
```


```python
print(dollars)
```

    <map object at 0x1041bb450>



```python
print(list(dollars))
```

    [112.00000000000001, 224.00000000000003, 336.00000000000006, 448.00000000000006]



```python
list(map(lambda x: 0.89*x, amounts))
```




    [89.0, 178.0, 267.0, 356.0]




```python

```

