# FetchApiJs
Just weird way to fetch api in javascript

# The Net Ninja Tutorial
```javascript
const getData = async (api) => {
	const response = await fetch(api)
	if(response.status !== 200) {
		throw new Error('fetch failed')
	}
	const data = await response.json()
	return data
}

getData('http://someapi.com/apiendpoint')
	.then(data => console.log('resolved: ', data))
	.catch(err => console.log('rejected: ', err.message))
```

# Simplified
```javascript
const getData = async (api) => {
	const response = await fetch(api)
	return await response.json()
}

getData('http://someapi.com/apiendpoint')
	.then(data => console.log('resolved: ', data))
	.catch(err => console.log('rejected: ', err.message))
```

# Extreme simplified
```javascript
const getData = async (api) => await fetch(api).then( async (response) => await response.json())

getData('http://someapi.com/apiendpoint')
	.then(data => console.log(data))
	.catch(err => console.warn(err.message))
```

# Crazy readability
```javascript
const getData = async (api) => await fetch(api)
.then(async (response) => await response.json()
	.then(data => console.log(data))
	.catch(err => console.warn(err.message)))
.catch(err => console.warn(err.message))
	
getData('http://someapi.com/apiendpoint')
```
# Custom reusable function
```javascript
// Assuming variable to store the data is storeVariable
let storeVariable;

const getData = async (api, callfn) => await fetch(api)
.then(async (response) => await response.json()
    	.then(data => callfn(data))
    	.catch(err => console.warn(err.message)))
.catch(err => console.warn(err.message))

// Pass in the variable with callback function
getData('http://someapi.com/apiendpoint', (data) => storeVariable = data)

// See the result
console.log(storeVariable)
```
