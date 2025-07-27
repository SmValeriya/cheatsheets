# Поширені функції JavaScript

- **Створити випадкові кольори**

``const generateRandomHexColor = () => '#' + Math.floor(Math.random() * 0xffffff).toString(16);
// or
const randomColor = () => `#${Math.random().toString(16).slice(2, 8).padEnd(6, '0')}`
``

- **Перетворити RGB to hex**

`const rgbToHex = (r, g, b) => "#" + ((1 << 24) + (r << 16) + (g << 8) + b).toString(16).slice(1);`

- **Перевпорядкувати масив**

`const shuffle = (arr) => arr.sort(() => Math.random() - 0.5);`

- **Визначити темну тему**

`const isDarkMode = () => window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches;`

- **Прокрутити до верху елемента**

`const scrollToTop = (element) => element.scrollIntoView({behavior: 'smooth', block: 'start'});`

- **Прокрутити до низа елемента**

`const scrollToBottom = (element) => element.scrollIntoView({behavior: 'smooth', block: 'end'});`

- **Визначити тип девайсу**

`const detectDeviceType = () =>  /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(
                                  navigator.userAgent
                                  ) ? 'Mobile' : 'Desktop';`

- **Отримати параметри з URL**

`const getParamsByUrl = (key) => {
  const url = new URL(location.href);
  return url.searchParams.get(key);
};`

- **Глибока копія об'єкта**

`const deepCopy = object => JSON.parse(JSON.stringify(object));`

- **Створити випадкову строку**

`const randomString = () => Math.random().toString(36).slice(2);`

- **Зробити великою кожну першу букву слів строки**

`const uppercaseWords = (str) => str.replace(/^(.)|\s+(.)/g, (c) => c.toUpperCase());`

- **Перетворити строку у camelCase**

`const toCamelCase = (str) => str.trim().replace(/[-_\s]+(.)?/g, (_, c) => (c ? c.toUpperCase() : ''));`

- **Видалити повторні значення у массиві**

`const removeDuplicates = (arr) => [...new Set(arr)];`

- **Зробити один массив з підмассивами**

`
const flat = (arr) =>
    [].concat.apply(
        [],
        arr.map((a) => (Array.isArray(a) ? flat(a) : a))
    )
// Or
const flat = (arr) => arr.reduce((a, b) => (Array.isArray(b) ? [...a, ...flat(b)] : [...a, b]), []);
`

- **Видалити хибні значення з массиву**

`const removeFalsy = (arr) => arr.filter(Boolean)`

- **Перевірити чи парне число**

`const isEven = num => num % 2 === 0`

- **Випадкове число з діапазону**

`const random = (min, max) => Math.floor(Math.random() * (max - min + 1) + min)`

- **Отримати середнє значення аргументів**

`const average = (...args) => args.reduce((a, b) => a + b) / args.length;`

- **Скинути усі кукі**

``const clearCookies = () => document.cookie.split(';').forEach((c) => (document.cookie = c.replace(/^ +/, '').replace(/=.*/, `=;expires=${new Date().toUTCString()};path=/`)))``

- **Обмежити частоту виконання функції (debouncing)**

``
const debounce = (func, delay) => {
  let timeout;
  return (...args) => {
    clearTimeout(timeout);
    timeout = setTimeout(() => func(...args), delay);
  };
};
``

- **Контроль частоти виконання функції протягом певного часу (throttling)**

``
const throttle = (func, limit) => {
  let lastFunc;
  let lastRan;
  return (...args) => {
    if (!lastRan) {
      func(...args);
      lastRan = Date.now();
    } else {
      clearTimeout(lastFunc);
      lastFunc = setTimeout(() => {
        if (Date.now() - lastRan >= limit) {
          func(...args);
          lastRan = Date.now();
        }
      }, limit - (Date.now() - lastRan));
    }
  };
};
``

- **Функція кешування результатів для швидкого повторного виклику**

``
const memoize = fn => {
  const cache = {};
  return (...args) => {
    const key = JSON.stringify(args);
    if (!cache[key]) cache[key] = fn(...args);
    return cache[key];
  };
};
``

- **Використання Intl для форматування валюти, дат та чисел**

``
const formatter = new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD' });
console.log(formatter.format(1000)); // $1,000.00
``