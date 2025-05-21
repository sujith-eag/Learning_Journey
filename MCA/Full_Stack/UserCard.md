`UserCard.js`

```jsx
import React from 'react';
import PropTypes from 'prop-types';

const UserCard = ({name,age}) =>{
	return(
		<div>
			<h2>{name}</h2>
			<p>Age: {age} years</p>	
		</div>	
	);
};

UserCard.propTyes={
	name: PropTypes.string.isRequired,
	age: PropTypes.number.isRequired
};

export default UserCard;

```