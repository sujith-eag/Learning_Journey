nstead of defining a one-off template for your UIs, React allows
you to create reusable UI components in JavaScript that you can use again and again on your sites.

> [!note]
> The name of the component has to be starting with Capital
> `import Welcome from './welcome';`



```jsx

import Reacr 'react';

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
