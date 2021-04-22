# Type vs Interface

typescript에서는 데이터 타입을 명시하는 방법으로 다음의 2가지 방법을 제공한다.
- type
- interface

기본적으로 둘은 비슷한 기능을 수행하나, 다음의 상황에서 둘은 차이점을 보인다
- `type` aliasing은 primitive type에 대해서도 적용 가능
  - `interface`의 경우 Object로 wrapping을 해야한다
- `type`의 경우 `interface`가 하지 못하는 `union type`이나 `tuple type`을 구현할 수 있다.
- `interface`의 경우 class 타입을 통해 `implements`를 하거나 `extends`키워드를 통해 확장할 수 있다.

```typescript
//interface 키워드를 이용한 타입 선언
//다음과 같이 primitive type 임에도 Object로 wrapping을 해야함
interface INumberData {value:number};
interface IStringData {value:string};

//같은 이름의 interface를 선언하여 declaration merging을 수행할 수 있음
interface INumberData {label:string};
let VNumberInstance:INumberData = {value:5,label:"this works"}

//type 키워드를 이용한 타입 선언
type TNumber = number
type TString = string

//type 키워드를 이용하여 Union 타입이나 Tuple 타입 선언을 통해 타입 확장 가능
type TUnionType = INumberData | IStringData
type TTupleExample = [INumberData,IStringData]

//extends 키워드를 통해 interface 확장 가능
interface IExtendSample extends INumberData {
    data:number
};

//class 타입을 통해 instantiate할 수 있는 타입 선언 가능
class CImplementSample implements IExtendSample{
    data: number
    value: number
    constructor(data:number,value:number){
        this.data= data;
        this.value =value;
    }
}

//class type은 aliasing이 안됨.
//다음의 라인은 에러를 유발함
type TImplementAliased = CImplementSample
```

개인적으로 interface는 데이터에 대한 OOP스타일의 접근방법이고, type은 FP 스타일의 관점으로 보인다.
