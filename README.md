<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=UTF-8">



</head>

<h1 style="text-align: center;">
	<span style="text-decoration: underline;">WCouchDB For Java</span>
</h1>
<p style="text-align: center;">WCouchDB is the most powerful
	&nbsp;java library project for CouchDB.</p>
<h2>
	<span style="text-decoration: underline; color: #339966;">Features:</span>
</h2>
<ul>

	<li>RESTFUL api.</li>
	<li>General Wrap for JSON results.</li>
	<li>Fasters Requests.</li>
	<li>Fasters Responses.</li>
	<li>Easy and convenient to use.</li>
</ul>
### Download Library
[WCouchDB Library](https://github.com/shaibenshim/WCouchDB/blob/master/WCouchDB/WCouchDB-1.0.jar?raw=true "WCouchDB jar")
<h2>
	<span style="text-decoration: underline;"><span
		style="color: #339966; text-decoration: underline;">Quick
			Guide:</span></span>
</h2>
<ul>
	<li>Set Config.</li>
	<li>Create New Database And Get Result.</li>
	<li>Create New Document With Gerante ID.</li>
	<li>Create New Document With Custom ID.</li>
	<li>Result Class</li>
	<li>Get UUIDs.</li>
	<li>Get Document.</li>
	<li>Get Result View.</li>
	<li>Update Document.</li>
</ul>
<h2>
	<span style="text-decoration: underline; color: #333333;"><span
		style="text-decoration: underline;">Set Config:</span></span>
</h2>

```java 
//Define your name, password and CouchDB url.
 String namePass="name:password";
  String url = "http://127.0.0.1:5984/";

//Create instance with ConfigBuilder. 
Config configStruct = newConfig(url,namePass); 
ConfigBuilder.getInstance(configStruct); 
```
<h2>
	<span style="text-decoration: underline; color: #333333;"><span
		style="text-decoration: underline;">Create New Database And Get
			Result:</span></span>
</h2>
```java
 //Created new and empty database will return the Result Object.
Result result = Q.createDatabase("db1"); 
//Printed Result Object 
{
"result":{
  "ok":true
},
"status":201
}

```

<h2>
	<span style="text-decoration: underline; color: #333333;"><span
		style="text-decoration: underline;">Create New Document With
			Gerante ID:</span></span>
</h2>
```java 
 // To create new database With Generate ID:
 // 1) Define existing database,
 // 2) Set JSONObject with parameters,
 // 3) Call to createDocument function :

String dataBase = "db1";
JSONObject data = newJSONObject(); 
data.put("integer", 0); 
data.put("String", "Hello Doc1");
data.put("jsonObject", new JSONObject().put("key", "value"));
data.put("jsonArray", new JSONArray().put(1).put("Hii").put(false));


Result result = Q.createDocument(dataBase, data);

 //Printed Result 
 {
"result":{
  "id":"e763959f2845da29ea37871398002a2d",
  "rev":"1-69902a74c7b8e93fe31fb81c606d81c1",
  "ok":true
},
"status":201
}
```

<h2>
	<span style="text-decoration: underline; color: #333333;"><span
		style="text-decoration: underline;">Create New Document With
			Custom ID:</span></span>
</h2>
```java 
// To create new database With Custom ID: 
// In your JSONObject data set doc._id for the key and String for value 
data.put(doc._id,"your custom id"); 
```

<h2>
	<span style="text-decoration: underline; color: #333333;"><span
		style="text-decoration: underline;">Result Class:</span></span>
</h2>

Result Class has 2 methods:
	<code>getStatus()</code>
	and
	<code>getResult()</code></br>
	
You get any http status for each response.</br>

<ul>
	<li>200 - OK</li>
	<li>201 - Create</li>
	<li>202 - Accepted</li>
	<li>301 - Premanetly</li>
	<li>304 - Not Modeified</li>
	<li>400 - Bad Request</li>
	<li>401 - Unauthorized</li>
	<li>403 - Forbidden</li>
	<li>404 - Not Found</li>
	<li>405 - Method Not Allowed</li>
	<li>409 - Conflict</li>
	<li>412 - Precondition Failed</li>
	<li>500 - Server Error</li>

</ul>
<code>getResult()</code> simply return the response in json format</br>

<h2>
	<span style="text-decoration: underline; color: #333333;"><span
		style="text-decoration: underline;">Get UUIDs</span></span>
</h2>
</br>

```java 
    UUID uuid = Q.getUUID();
	List<UUIDSStruct> uuids = uuid.getUuids();
```

	
<h2>
	<span style="text-decoration: underline; color: #333333;"><span
		style="text-decoration: underline;">Get Document</span></span>
</h2>
</br>

```java 
    String dbName = "db1";
    String docName = "doc1";

	Document document = Q.getDocument(dbName, docName);
	
	//Printed Result
{
 "_id":"e763959f2845da29ea378713980039f2",
 "_rev":"1-5bd0c98effb74f2fd4c2edefdfaa886f",
 "integer":0,
 "String":"Hello Doc1",
 "jsonObject":{
   "key":"value"
 },
 "jsonArray":[
 1,
 "Hii",
 false
 ]
}
```
<h2>
	<span style="text-decoration: underline; color: #333333;"><span
		style="text-decoration: underline;">Get Result View</span></span>
</h2>
</br>
```java 
    String dbName = "db1";
	String designDoc = "design1";
	String view = "view1";

	View getView = Q.getView(dbName, designDoc, view);

	List<ViewRow> rows = getView.getRows();

	for (int i = 0; i < rows.size(); i++) {
	    System.out.println(rows.get(i).getValue());
	}

```
You can also get view by query key and keys:
<code>Q.getViewByKey(dbName, designDoc, view, key, includeDocs);
</code>
</br>
For getting view by keys set list of keys
<code>
    List<String> keys = new ArrayList<String>();
	keys.add("key1");
	keys.add("key2");
	keys.add("key3");
	Q.getViewByKeys("db1", "designDoc1", "view1", keys, true);
</code>
</body>
</html>
