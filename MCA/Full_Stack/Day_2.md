nstead of defining a one-off template for your UIs, React allows
you to create reusable UI components in JavaScript that you can use again and again on your sites.

> [!note]
> The name of the component has to be starting with Capital
> `import Welcome from './welcome';`

___
### React JS Keys

Uniquely identifying elements in a list for efficient rendering

```jsx

import React from 'react';

const products = [
	{ id: 'P1', name: 'Wireless Mouse', price: '$25'},
	{ id: 'P2', name: 'Mechanical Keyboard', price: '$80'},
	{ id: 'P3', name: 'USB-C Hub', price: '$40'},
];

const ProductCatalog = () => {
	return (
		<ul>
		{products.map( (product)=> (
			<li key={product.id}>
				<strong>{product.name}</strong> : {product.price}
			</li>
		))}
		</ul>
	);
};

export default ProductCatalog;
```

```jsx
const items = ['Apple', 'Bannana', 'Cherry'];

items.map( (fruit, index) => 
	<li key={fruit}>{fruit}</li>);
	
```

```jsx
import React from 'react';

const TodoList = () => {
	const tasks = [
		{id: 101, text: 'Complete React assignment'},
		{id:102, text: 'Read a new article'},
		{id:103, text: 'Go for run'}
	];
	
	return(
		<ul>
			{tasks.map( 
				(task) => (
					<li key={task.id}>{task.text}</li>
				)
			 )}
		</ul>	
	);
}
export default TodoList;
```

```jsx
import React from 'react';

const TodoList = () => {
	const tasks = [
		{id: 101, text: 'Complete React assignment', res: ['a', 'b', 'c']},
		{id:102, text: 'Read a new article', res: ['b', 'd', 'e']},
		{id:103, text: 'Go for run', res: ['c', 'f', 'g']}
	];
	
	return(
		<ul>
			{tasks.map( 
				(task) => (
					<li key={task.id}>{task.text}
                        <ol>
                            {(task.res).map( (rs, index) => (
                                <li key={index}>{rs}</li>)
                            )}
                        </ol>
                    </li>
				)
			 )}
		</ul>	
	);
}
export default TodoList;
```

```
- Complete React assignment
    1. a
    2. b
    3. c
- Read a new article
    1. b
    2. d
    3. e
- Go for run
    1. c
    2. f
    3. g
```

```jsx

const StudentList = () => {
	const students = [
		{roll:'A01', name: 'Anitha', res: ['a', 'b', 'c']},
		{roll:'A02', name: 'Rahul', res: ['b', 'd', 'e']},
		{roll:'A03', name: 'Saniya', res: ['c', 'f', 'g']}
	];
    
    return(
        <div>
            <ul>
                {students.map( (ob) => (
                    <li >Roll No:{ob.roll}, Name : {ob.name}</li>
                ))}
            </ul>
        
        </div>  
    );
}

export default StudentList;
```

```
- Roll No:A01, Name : Anitha
- Roll No:A02, Name : Rahul
- Roll No:A03, Name : Saniya
```

____

