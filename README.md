# WebStorageCache [Draft]

  <a href='https://gitter.im/WQTeam/web-storage-cache'>
    <img src='https://badges.gitter.im/Join%20Chat.svg' alt='Gitter Chat' />
  </a>

  WebStorageCache backed by [Storage API](http://www.w3.org/TR/webstorage/#storage).
  
  [中文版](https://github.com/WQTeam/web-storage-cache/blob/master/README_zh_CN.md)
  

# Usage
```javascript
  var wsCache = new WebStorageCache();
  
  // cache 'wqteam' at 'username', expired in 100 seconds
  wsCache.set('username', 'wqteam', {exp : 100});
  
  // deadline in  May 18 2015
  wsCache.set('username', 'wqteam', {exp : new Date('2015 5 18')});
  
  // get 'username' 
  wsCache.get('username');
  
  // cache an object literal - default uses JSON.stringify under the hood
  wsCache.set('user', { name: 'Wu', organization: 'wqteam'});
  
  // Get the cache object - default uses JSON.parse under the hood
  var user = wsCache.get('user');
  alert(user.name + ' belongs to ' + user.organization);
  
  // delete 'username'
  wsCache.delete('username');
  
  // Clear all keys
  wsCache.clear();
  
  // Set a new expiration time for an existing key.
  wsCache.touch('username',  {exp : 1000});
  
  // Add key-value item to cache, success only when the key is not exists in cache
  wsCache.add('username2', 'wqteam', 1000);
  
  // Replace the key's data item in cache, success only when the key's data item is exists in cache.
  wsCache.replace('username', 'new wqteam', {exp : 1000});
  
  // check if the 'storage' supported by the user browser. if not all the  WebStorageCache API method will do noting.
  wsCache.isSupported();
  
```
# API

## Constructor
```javascript
var wsCache = new WebStorageCache({
  // [option] 'localStorage', 'sessionStorage', window.localStorage, window.sessionStorage or 
  // other storage instance implement [Storage API].
  // default 'localStorage'.
  storage: 'localStorage',
  // [option] defalut `serialize` uses JSON.stringify under the hood, 
  // and 'deserialize' uses JSON.parse under the hood.
  serializer: serializer,
  // [option] //An expiration time, in seconds. default never .
  exp: Infinity,
  // [option] handler quotaExceed Error. default do noting.
  quotaExceedHandler: quotaExceedHandler 
}); 
```


