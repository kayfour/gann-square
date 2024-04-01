# Gann Square

날짜 기반 Gann Square 구축 도구입니다.

[example.svg](example/proton-m-launches.svg)

### Features

* 큰 크기 지원
  
* 경제 분야에서의 일반적인 사용에도 불구하고, 이 프로그램은 숫자 대신 날짜 시퀀스를 제공할 수 있습니다. 이를 통해 중요한 날짜의 분포를 분석할 수 있습니다.

* 시각화 지원 (기본 Gann 시각화 및 셀 하이라이팅)


### How to use  

클래식 Gann square를 구축하려면:
 
```
python gann.py -o <output file name> -s <square size>
```  
  
`<square size>` 는 각 축의 셀 수입니다.
    
날짜 기반의 Gann square를 구축하려면:

```  
python gann.py -o <output file name> -a <base date> -b <final date> -m <path to list of dates to mark>
```  

입력 날짜 형식 "dd/MM/yyyy"      
셀을 하이라이트하려면 구조가 다음과 같은 .json 파일을 제공합니다:    

``` json
[
    {
        "description": "<description>",
        "color": "<color>",
        "data_path": "<path to dates>"
    },
    {
        "description": "<description>",
        "color": "<color>",
        "data_path": "<path to dates>"
    }
]
```  

`<path to dates>` 는 하이라이트할 날짜가 있는 .txt 파일로 대체해야 합니다.
형식: 

```  
<date1>  
<date2>  
...
```  
  
성능 문제를 피하기 위해 큰 스퀘어를 조각별로 구축하는 것이 권장됩니다. 
각 셀은 그 위치와 이전 셀에 의해서만 결정될 수 있으며, 이전 셀이 필요하지 않습니다.  

날짜 기반의 Gann 부분 스퀘어를 구축하려면:

```  
python gann.py -o <output file name> -a <base date> -b <final date> -m <path to list of dates to mark> -r "<left>;<bottom>;<right>;<up>"
```  

Gann square는 프로그램 내에서 다음과 같은 좌표 시스템을 가지고 있습니다:

```  
 ____ ____ ____
|-1 1|0  1|1  1|
|-1 0|0  0|1  0|
|-1-1|0 -1|1 -1|

```  
  
So when you specify `-r "-5;-5;5;5"`, that will cut the center square with size: 11x11.
따라서 '-r "-5;-5;5;5"' 를 지정하면, 크기가 11x11인 중앙 스퀘어를 자릅니다.


### Example  

cmd 실행:

```  
$ python gann.py -o "example/proton-m-launches.svg" -a "07/04/2001" -b "19/03/2015" -m "example/data.json"
```  

proton-m-launches.html은 지난 14년간 'Proton-M'의 성공적이고 실패한 발사를 보여줍니다.

### Requirements

* Python 3

# LICENSE
This project is licensed under the terms of the MIT license. (see LICENSE.txt in the root)
