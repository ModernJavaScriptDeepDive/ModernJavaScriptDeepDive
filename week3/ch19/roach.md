# Prototype

자바스크립트가 프로토타입을 유지해서 상속을 유지하는건, 기존의 객체기반의 프로그래밍보다 강력하다고 하는데.. 흐음 ㅋㅋ 잘모르겠지만 아래와 같은 코드가 좋다고 생각한다.

```javascript
function Chicken(fly) {
  this.fly = fly;
}

const chicken1 = new Chicken(() => {
  console.log("i can fly");
});

const chicken2 = new Chicken(() => {
  console.log("i can fly");
});

chicken1.fly();
chicken2.fly();

console.log(chicken1.fly === chicken2.fly);

Chicken.prototype.we = () => {
  console.log("i can fly");
};

const chicken3 = new Chicken();

const chicken4 = new Chicken();

chicken3.we();
chicken4.we();

console.log(chicken3.we === chicken4.we);
```

prototype 에 정의해놓은것을 공유하기 때문에, 같은 Function 을 중복해서 메모리상에 할당할 필요가 없다. 근데 사실 이것도 잘해야 하는것이 prototype 에 걸어놓은 것들이 변경될 수도 있는 것들이라면, Side-Effect 를 충분히 발생시킬 수 있으므로, 잘 걸지 않는다면 원치않은 효과를 발생시킬 수 있다고 생각한다.
