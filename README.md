# fetchApiJS
Just weird way to fetch api

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
	.then( data => console.log('resolved: ', data))
	.catch( err => console.log('rejected: ', err.message))
```

# Simplified
```javascript
const getData = async (api) => {
	const response = await fetch(api)
	return await response.json()
}

getData('http://someapi.com/apiendpoint')
	.then( data => console.log('resolved: ', data))
	.catch( err => console.log('rejected: ', err.message))
```

# Extreme simplified
```javascript
const getData = async (api) => await fetch(api).then( async (response) => await response.json())

getData('http://someapi.com/apiendpoint')
	.then( data => console.log('resolved: ', data))
	.catch( err => console.log('rejected: ', err.message))
```

# Crazy readability
```javascript
const getData = async (api) => await fetch(api).then( async (response) => await response.json()
	.then( data => console.log('resolved: ', data))
	.catch( err => console.log('rejected: ', err.message)))
	
getData('http://someapi.com/apiendpoint')
```
