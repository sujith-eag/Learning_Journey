
```jsx
import { useState } from 'react';

function TermsOfUse(){
	const [showTerm, setShowTerm] = useState(false);
	
	function handleShowTerms() {
		setShowTerms(true);
	}
	
	let paragraph;
	
	if(showTerms) {
		paragraph = <p>By continuing you accept the conditions</p>;
	}
	
	return(
		<section>
			<button onClick={handleShowTerms}>
				Show Terms of Use Summary
			</button>
			{paragraph}
		</section>
	);
} 
```


If showTerms is false, paragraph stores the value undefined
and nothing is rendered to the DOM. Therefore, inserting null or undefined in JSX code leads to nothing being outputted by React. But if showTerms is true, the complete paragraph is saved as a value and outputted in the DOM.
















