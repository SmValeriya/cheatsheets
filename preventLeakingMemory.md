# Запобігання витоку пам'яті

- **Глобальні змінні**

Не використовуйте глобальні змінні без необхідності. Глобальні змінні створюються, коли присвоюється значення без попереднього оголошення let, const або var


```
function calculateArea(width, height) {
  // Помилково створена глобальна змінна 'area'
  area = width * height; 
  return area;
}
calculateArea(10, 5);
```

- **Таймери**

Видаляйте таймери, коли вони вже не потрібні, оскільки вони можуть блокувати видалення вже не потрібної інформації

```
let userData = {
  name: "John",
  age: 25
};

let intervalId = setInterval(() => {
  userData.age += 1;
}, 5000);
// Далі по коду, коли інтервал вже не потрібен
clearInterval(intervalId);
```

- **Замикання**

```
function createCountdown(start) {
  let count = start;

  return function() {
    return count--;
  };
}

let countdownFrom10 = createCountdown(10);

// Якщо не прибрати посилання countdownFrom10, буде зберігатись посилання на змінну count

countdownFrom10 = null;
```

- **Підписка на події**

Перед тим, як видалити елемент з DOM, потрібно прибрати слухача подій з цього елемента

```
const button = document.getElementById('myButton');

function handleClick() {
  console.log('Button was clicked!');
}

button.addEventListener('click', handleClick);

// Далі по коду, коли вже видаляємо елемент
button.removeEventListener('click', handleClick);
button.remove();
```

- **Недосяжні DOM елементи**

При видаленні елементу з DOM, якщо він більше не потрібен, не забуваємо видалити і посилання на нього у коді

```
let listItem = document.getElementById('itemToRemove');
listItem.remove();
listItem = null;
```

- **Websockets і зовнішні підключення**

Коли розриваєм зв'язок Websocket'а не забуваєм відписатися від подій, як у прикладі нижче

```
let socket = new WebSocket('ws://example.com/updates');

socket.onmessage = function(event) {
  console.log(`Received update: ${event.data}`);
};

// Далі по коду, коли зв'язок розірваний
socket.close();
socket.onmessage = null;
socket = null;
```

[Повну статтю про виток пам'яті можно прочитати за цим посиланням](https://blog.stackademic.com/your-js-app-is-leaking-memory-and-you-dont-know-914e64ed07c7)