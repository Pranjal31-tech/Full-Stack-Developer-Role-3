# Full-Stack-Developer-Role-3


1.What will be the output of the following code?
console.log(1 + "1");
console.log(1 - "1"); console.log(1 + true); console.log(1 + undefined);

Output:

js "11"
0
2
NaN

Explanation:

•	1 + "1" → "1" is a string, so JavaScript performs implicit type coercion and converts 1 to "1", resulting in string concatenation: "11".
•	1 - "1" → The - operator triggers numeric conversion, converting "1" to 1, so 1 -
1 = 0.
•	1 + true → true is coerced to 1, so 1 + 1 = 2.
•	1 + undefined → undefined cannot be converted to a valid number, resulting in
NaN.


2.	How do you center a div both vertically and horizontally without using flexbox or grid?
Using absolute positioning and transform:

.parent {
position: relative;
height: 100vh; /* Adjust as needed */
}

.child {
position: absolute; top: 50%;
left: 50%;
transform: translate(-50%, -50%);
}

Explanation:

•	top: 50% and left: 50% move the div to the center of its parent.
•	transform: translate(-50%, -50%) shifts it back by half its width and height.

 
3.	What will be the output of the following loop?
for (var i = 0; i < 3; i++) {
setTimeout(() => console.log(i), 1000);
}

Output after 1 second:

js 
3
3
3

Explanation:

•	var is function-scoped, so i is shared across all iterations.
•	By the time setTimeout executes, the loop has already finished, and i = 3.
•	To fix this, use let (block-scoped) or an IIFE:

js CopyEdit
for (let i = 0; i < 3; i++) {
setTimeout(() => console.log(i), 1000);
}


4.	How do you reverse a string without using .reverse()?
Using a for loop:

function reverseString(str) { let reversed = "";
for (let i = str.length - 1; i >= 0; i--) { reversed += str[i];
}
return reversed;
}
console.log(reverseString("hello")); // "olleh"

Using recursion:

function reverse(str) {
return str ? reverse(str.slice(1)) + str[0] : "";
}

Using reduce():

js 
const reverseStr = str => str.split('').reduce((rev, char) => char + rev, '');

 
5.	What will be the output of the following React code?
const [count, setCount] = React.useState(0);

function increment() { setCount(count + 1);
setCount(count + 1);
}

Output: Clicking the button increases count by 1, not 2.
Explanation:

•	setCount(count + 1) is based on the current count value, which doesn't update immediately.
•	To fix this, use a function-based update:

jsx CopyEdit
setCount(prevCount => prevCount + 1); setCount(prevCount => prevCount + 1);

This ensures count updates correctly.


6.	What will be the output of these expressions?
console.log([] + []);
console.log([] + {});
console.log({} + []);
console.log({} + {});

Output:

""
"[object Object]" 0
"[object Object][object Object]"

Explanation:

•	[] + [] → Empty arrays are converted to empty strings: "".
•	[] + {} → {} is converted to a string: "[object Object]".
•	{} at the start of a line is treated as an empty block, so {} + [] is 0.
•	{} + {} → Both objects are converted to "[object Object]", concatenating them.


7.	How do you debounce a function?
function debounce(func, delay) { let timer;
return function(...args) {
 
clearTimeout(timer);
timer = setTimeout(() => func.apply(this, args), delay);
};
}

const log = debounce(() => console.log("Debounced!"), 1000); window.addEventListener("resize", log);

Explanation: Delays function execution until after delay milliseconds of inactivity.


8.	How can you implement smooth scrolling?
Using JavaScript:

document.querySelector("#target").scrollIntoView({ behavior: "smooth" });

Using CSS:

css CopyEdit html {
scroll-behavior: smooth;
}


9.	What will be the output of this code?
console.log(typeof null); console.log(typeof NaN); console.log(typeof function() {}); console.log(typeof []); console.log(Array.isArray([]));

Output:

"object" "number" "function" "object" true

Explanation:

•	null is a known JavaScript bug; it's object.
•	NaN is of type number.
•	Functions have typeof "function".
•	Arrays are objects, but Array.isArray([]) correctly identifies them.


10.	What will be the output of these logical expressions?
 
console.log("Hello" || "World"); console.log("" || "World"); console.log(0 || 1);
console.log(0 && 1);
console.log(1 && 2);

Output:

"Hello" "World" 1
0
2

Explanation:

•	|| returns the first truthy value.
•	&& returns the first falsy value or the last operand if all are truthy.


11.	Event delegation vs. bubbling?
•	Bubbling: Events propagate from child to parent.
•	Delegation: Attaching a listener to a parent and checking event target.

Example:

document.getElementById("parent").addEventListener("click", function(event)
{
if (event.target.matches(".child")) { console.log("Child clicked!");
}
});


12.	How do you create a triangle using CSS?
.triangle {
width: 0;
height: 0;
border-left: 50px solid transparent; border-right: 50px solid transparent; border-bottom: 100px solid red;
}

Explanation: Uses border to create a triangle.


13.	Deep cloning without JSON.parse(JSON.stringify(obj))?

function deepClone(obj) {
return structuredClone(obj);
 
}

Or using recursion:

function deepClone(obj) {
if (typeof obj !== "object" || obj === null) return obj; let copy = Array.isArray(obj) ? [] : {};
for (let key in obj) {
copy[key] = deepClone(obj[key]);
}
return copy;
}


14.	Deep Clone of an Object in JavaScript without JSON methods: To implement a deep clone of an object in JavaScript without using JSON.parse(JSON.stringify(obj)), you can use a recursive approach combined with Object.assign() or the spread operator (...). Here's an example using recursion:
javascript
function deepClone(obj) {
    if (obj === null || typeof obj !== 'object') {
        return obj;
    }
    
    let clone = Array.isArray(obj) ? [] : {};
    
    for (let key in obj) {
        if (obj.hasOwnProperty(key)) {
            clone[key] = deepClone(obj[key]);
        }
    }
    
    return clone;
}
This function deepClone() recursively clones nested objects and arrays. It handles various edge cases and ensures a deep copy without using JSON serialization methods.
15.	React Code Output and Explanation:
javascript
function App() {
    const [count, setCount] = React.useState(0);
    React.useEffect(() => {
        console.log("Effect triggered");
    }, [count]);
    return <button onClick={() => setCount(count)}>Click me</button>;
}
•	Clicking the button triggers setCount(count), which updates the count state to its current value (count doesn't change).
•	Since the dependency array of useEffect includes [count], the effect runs whenever count changes. However, in this case, count remains unchanged (0), so the effect won't log anything immediately upon button click.
16.	Updating State Variable Directly in React: If you update a state variable directly in React like this.state.count = 5, React won't detect the change, leading to potential bugs and UI inconsistencies. Always use setState() or the functional update form provided by useState() hooks to update state in React.
17.	Lazy Loading of Images in JavaScript: Lazy loading of images can be achieved using the IntersectionObserver API in JavaScript. Here's a basic example:
javascript
const images = document.querySelectorAll('img.lazy');

const options = {
    root: null,
    rootMargin: '0px',
    threshold: 0.1
};

const observer = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            const image = entry.target;
            image.src = image.dataset.src;
            observer.unobserve(image);
        }
    });
}, options);

images.forEach(image => {
    observer.observe(image);
});
This code snippet uses IntersectionObserver to detect when images come into view, then loads the image source (data-src) when they are near the viewport, improving performance by loading images only when needed.
18.	Object Freezing in JavaScript:
javascript
let obj = { a: 1, b: 2 };
Object.freeze(obj);
obj.a = 5;
console.log(obj.a); // Output: 1
•	Object.freeze() makes an object immutable.
•	Attempting to modify a frozen object (obj.a = 5;) does not change its properties.
•	Therefore, console.log(obj.a); outputs 1, as the object remains unchanged after freezing.
19.	Sticky Header in CSS: To create a sticky header in CSS that remains fixed at the top when scrolling, you can use the following CSS:
css
.sticky-header {
    position: sticky;
    top: 0;
    background-color: #ffffff; /* Adjust background color as needed */
    z-index: 1000; /* Adjust z-index if needed */
}
Apply the sticky-header class to your header element (<header class="sticky-header">) to make it sticky.
20.	Output of the Snippet:
javascript
console.log(0.1 + 0.2 === 0.3); // Output: false
console.log((0.1 + 0.2).toFixed(2) === "0.30"); // Output: true
•	JavaScript floating point arithmetic can sometimes lead to precision issues.
•	0.1 + 0.2 === 0.3 evaluates to false due to precision loss in floating-point arithmetic.
•	(0.1 + 0.2).toFixed(2) === "0.30" evaluates to true because toFixed(2) converts the result to a string with two decimal places, which matches "0.30".

