---
description: How to build your live streaming web app with Uiza’s API using React and Java
---

# Java Live Streaming App

Uiza provides intuitive APIs, which simplifies the integration of live streaming functionality into your platform. This guide is a step-by-step tutorial on how to build your live streaming app with Uiza’s APIs. The web app will have two components: the broadcaster web app, to start a stream, and the viewer app, to list all broadcasts and playback the broadcast.

## Components of our live streaming app

Sample code is provided below on how to build a simple web app to call on Uiza’s API. The language used for web app is Javascript.

#### Uiza Streaming Concept

To understand the flow of the this tutorial, following terminologies are explained by the graph below. 

![](https://i.imgur.com/HQeo1jG.png)

During this documentation, broadcast, live streaming and streaming will be usede interchangeably.

#### Building a Live streaming Web App with Uiza

To have a live streaming app, we have to distinguish between a broadcaster and a viewer. A broadcaster streams the live stream and a viewer watches the live stream - this is a one way interaction channel, hence we have to build 2 separate pages: a broadcasting page and a viewer page. Tha broadcaster needs to start a broadcast through a stream URL and key, while the viewer sees the active live streams and can watch them through the web app.

## Building the live streaming JAVA app \(Backend\)

### Step 1. Getting started with Uiza Java application

To start a broadcast with Uiza Java App, we will need to configure stream\_url and stream\_key in application propeties file.

We need an API key to access Uiza's services. To get your API key, create an account at Uiza here: [Sign Up Link](https://id.uiza.io/register). Once you are in the developer console, you will see your API key. Configured your API key and URL in application properties as below.

We have created Java because we can not pass API key through browser. If we pass API key through browser then anyone can stole our API key and use Uiza api. So using JAVA app, we are storing this API key in the JAVA property file and calling Uiza api from Java App.

```text
application.uiza.url= https://api.uiza./v1/live_entities
application.uiza.authorization-token="API Key"
```

### Step 2. Deploy/Run Java App

Download the Java sample code at [Github link](https://github.com/uizaio/uiza-live-java-server-integration)

1. Go To Project Directory

   ```text
   cd uiza
   ```

2. Run below command

   ```text
   mvn clean install
   ```

3. After step 2 finishes installation, go to `target` directory inside the project. 

   ```text
   cd target
   ```

4. Run the below command to run java application. Java application will run 8080 port.

   ```text
   java -jar uiza-0.0.1-SNAPSHOT.jar
   ```

### Step 3. This guide will help you create a simple REST service using Spring Boot.

In this guide, we will create three services using proper URIs and HTTP methods:

* @GetMapping\("/app/live/entities"\): You can retrieve the live entities using request method Get and example uri /app/live/entities.
* @GetMapping\("/app/live/entities/{id}"\): You can retrieve a specific live entity using request method Get and example uri /app/live/entities/1.
* @PostMapping\("/app/live/entities"\) : You can create a live entity by sending a POST request to URI /app/live/entities

#### Using appropriate Request Methods

Always use HTTP Methods. Best practices with respect to each HTTP method is described below:

* `GET` : Should not update anything. Should be idempotent \(same result in multiple calls\). Possible Return Codes 200 \(OK\) + 404 \(NOT FOUND\) +400 \(BAD REQUEST\)
* `POST` : Should create new resource. Ideally return JSON with link to newly created resource. Same return codes as get possible. In addition : Return code 201 \(CREATED\) is possible.
* `PUT` : Update a known resource. ex: update client details. Possible Return Codes : 200\(OK\)
* `DELETE` : Used to delete a resource.

#### Project Structure

Following screenshot shows the structure of the project we have created. ![](https://i.imgur.com/Zvtz1E2.png) **A few details:**

* **LiveEntityResource.java** - Rest controller exposing all the three service methods discussed above.
* **LiveEntity.java** - Business Logic for the application.
* **UizaApplication.java** - Launcher for the Spring Boot Application. To run the application, just launch this file as Java Application.
* **pom.xml** - Contains all the dependencies needed to build this project. We will use Spring Boot Starter Web.

#### Adding Couple of GET Rest Services

The Rest Service LiveEntityResource exposes couple of get services.

@Autowired private RestTemplate restTemplate : We are using Spring Autowiring to wire the RestTemplate service into the LiveEntityResource. This rest template will use for call Uiza server api to get/create live entity. @Value\("${application.uiza.url}"\) private String ulzaUrl : Use the uiza server url that we have configured in step1.

@PathVariable String id: Value of live entity id from the uri will be mapped to this parameter. package com.uiza.api.rest;

```text
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.CrossOrigin;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.client.RestTemplate;

import com.uiza.api.dto.GetLiveEntityResponse;
import com.uiza.api.dto.LiveEntity;

@CrossOrigin(origins = "*")
@RestController
@RequestMapping("/app/live/entities")
public class LiveEntityResource {

    @Autowired
    private RestTemplate restTemplate;

    @Value("${application.uiza.url}")
    private String ulzaUrl;

    @GetMapping
    public GetLiveEntityResponse getLiveEntities() {

        ResponseEntity<GetLiveEntityResponse> responseEntity = restTemplate.getForEntity(ulzaUrl,
                GetLiveEntityResponse.class);

        return responseEntity.getBody();
    }

    @GetMapping("/{id}")
    public LiveEntity getLiveEntities(@PathVariable String id) {

        ResponseEntity<LiveEntity> responseEntity = restTemplate.getForEntity(ulzaUrl + "/" + id, LiveEntity.class);

        return responseEntity.getBody();
    }

}
```

**Executing the Get Service for retrieve all live Using Postman.**

We will fire a request to [http://localhost:8080/app/live/entities](http://localhost:8080/app/live/entities) to test the service. Response is as shown below.

```text
[{
     "id": "2b970a39-874a-4d2a-be8a-fd445646d74c",
     "user_id": "uiza",
     "app_id": "uiza",
     "name": "Test Event",
     "description": "Event for Test",
     "region": "in-bangalore-1",
     "status": "init",
     "created_at": "2019-10-03T17:34:49Z",
     "updated_at": "2019-10-03T17:34:49Z"
}]
```

**Executing the Get Service to retrieve live entity by id Using Postman**

We will fire a request to [http://localhost:8080/app/live/entities/2b970a39-874a-4d2a-be8a-fd445646d74c](http://localhost:8080/app/live/entities/2b970a39-874a-4d2a-be8a-fd445646d74c) to test the service. Response is as shown below.

```text
{
     "id": "2b970a39-874a-4d2a-be8a-fd445646d74c",
     "user_id": "uiza",
     "app_id": "uiza",
     "name": "Test Event",
     "description": "Event for Test",
     "region": "in-bangalore-1",
     "status": "init",
     "created_at": "2019-10-03T17:34:49Z",
     "updated_at": "2019-10-03T17:34:49Z"
}
```

#### Adding a POST Rest Service

A POST Service should return a status of created \(201\) when the resource creation is successful.

@PostMapping\("/app/live/entities"\): Mapping a url for the POST Request @RequestBody LiveEntity liveEntity: Using Binding to bind the body of the request to LiveEntity object. responseEntity.getBody\(\): Return a status of created. Also return the location of created resource as a Response Header.

```text
    @PostMapping
    public LiveEntity createLiveEntity(@RequestBody LiveEntity liveEntity) {

        ResponseEntity<LiveEntity> responseEntity = restTemplate.postForEntity(ulzaUrl, liveEntity, LiveEntity.class);

        return responseEntity.getBody();
    }
```

**Executing a POST Rest Service**

Example Request is shown below. It contains all the details to create a live entity.

```text
{
  "name": "Demo",
  "description": "AFF CUP",
  "region": "in-bangalore-1"
}
```

Example Response is shown below. It contains all the details that has been created for live entity.

```text
{
     "id": "2b970a39-874a-4d2a-be8a-fd445646d74c",
     "user_id": "uiza",
     "app_id": "uiza",
     "name": "Test Event",
     "description": "Event for Test",
     "region": "in-bangalore-1",
     "status": "init",
     "created_at": "2019-10-03T17:34:49Z",
     "updated_at": "2019-10-03T17:34:49Z"
}
```

#### Modification in live entity

* Suppose if we have to add new field in live entity then we have to do as below example.
* For example, If we have to add new field\(abc\) in live entity then we have to do below modification in LiveEntity.java

```javascript
private String abc;
public String getAbc(){ return abc; }
public void setAbc(String abc){ this.abc = abc; }
```

## Building the live streaming app \(front-end part\)

```text


## Step 1. Creating a new Project and install dependencies
To build a broadcast web app, we start with creating a new react web application.
Let us create a brand new application. 
Open terminal / command prompt and execute the below lines to create a starter app: 

1. Create a new project
```



### Step 1. Creating a new Project and install dependencies

To build a broadcast web app, we start with creating a new react web application.

Let us create a brand new application. 

Open terminal / command prompt and execute the below lines to create a starter app: 

#### 1. Create a new project

To build a broadcast web app, we start with creating a new react web application. Let us create a brand new application. Open terminal / command prompt and execute the below lines to create a starter app: 

`npx create-react-app uiza`

#### 2. Get into the project directory

`cd uiza`

#### 3. Start the development server.

`npm start`

#### Getting started with Uiza

To start a broadcast with Uiza we will need to do two things:

1. Create a live entity in Uiza servers.
2. Get the stream\_url and stream\_key for this entity.

#### Install program dependencies

To increase the readability of this tutorial, we use the Axios library to send requests to the Uiza server. Install Axios with the following command:

```npm install axios```

To play the video stream we will need a player control. Install react-player with the following command:

```npm install react-player```

### Step 2. Make changes to the App.js

Open the \`App.js\` file in the \`src\` directory.

#### Import repositories

Import react, router, react video player and css file.

```javascript
import React, { Component } from 'react';
import ReactPlayer from 'react-player';
import './App.css';
import {
  BrowserRouter as Router,
  Switch,
  Route,
  Link,
  useParams
} from "react-router-dom";
```

We need an JAVA API to access Uiza's services.

```javascript
const url = "https://api.uiza.sh/app/live/entities";
const default_headers = {
  "Content-Type": "application/json"
}
```

Then we import axios to send get and post requests:

```javascript
const  axios  =  require('axios').default;
```

#### Paging and navigation.

We divide the app into two parts: 

1. Broadcast Page: Will contain the functionality to create a new broadcast.
2. View Page: This will display all broadcasts currently in the system, with online broadcasts as a green tile and offline broadcasts as an orange-red.

### Step 3. Building the Broadcast Page

Let us start with the broadcast page design.

#### Creating default states

We use application-wide states that can be displayed in the application, and manipulated at run-time. As you can see, we can set default values with states. Our default region value is `in-bangalore-1`

```javascript
state  = {
    message:  '',
    region_value:  'in-bangalore-1',
    broadcast_url:  '',
    broadcast_key:  ''
};
```

#### Define a function to start a broadcast

We define this function as `start_broadcast`. We clear the states and set the message state to `fetching`. Then we start loading the information.

```javascript
this.setState({message: "Fetching"});
this.setState({broadcast_url: ""});
this.setState({broadcast_key: ""});
```

Now we set the parameters, so that we can make the `create entity` call. The below structure contains all the information of the HTTP request that we pass to Axios. As you can see, we make use of the `region_value` state to set the region to a supported value.

```javascript
var broadcast_create_options = {
  "method": "post",
  "url": "https://api.uiza.sh/api/v5/live/entities",
  "headers": default_headers,
  "data": {
        "name": 'Demo app',
        "region": this.state.region_value,
        "description": 'Application description'
 }
};
```

Now let's create the polling call structure so that we don't end up creating the same structure from the loop. As you can see it will be a `GET` request. Authorization header will expect your API key.

```javascript
var broadcast_polling_options = {
  "method": "get",
  "headers": default_headers,
  "data": {
      "name": 'Demo app',
      "region": this.state.region_value,
      "description": 'Application description'
    }
};
```

We make a `POST` request to create an entity.

```javascript
var create_response = await axios(broadcast_create_options);
console.log('Response Received')
```

The call returns the entity `id` in the response.

```javascript
 var broadcast_id = create_response.data.id;
 this.setState({message: 'broadcast Created: '+ broadcast_id});
```

The `GET` method takes the entity `id` and returns the broadcast information \(including the stream URL and key\).

```javascript
broadcast_polling_options["url"] = url + "/" + broadcast_id;
```

To get the stream URL and key, the entity has to be in a `ready` state. We use setInterval to poll the API every 3 seconds to check the status of the entity using `response.data.status` The initial status of an entity is `init`. When the server is ready with a stream URL and key, the status becomes `ready`

If the status is not`ready` yet, we continue polling and the current state of `message` will be set to `Polling`

Once the status is `ready` we can extract `url` and `key` from the response.

`self.setState({ message: 'Polling' + '.'.repeat(1 + counter%3) });`

The above code creates a nice text animation so that we know the program is not stuck and is working.

```javascript
var counter = 0;
var self = this;
var poll_interval = setInterval(async function() {
  try {
    var response = await axios(broadcast_polling_options);
    if (response.data.status === "ready") {
      self.setState({ message: "Stream is now ready" });
      self.setState({ broadcast_url: "URL: " + response.data.ingest.url });
      self.setState({ broadcast_key: "Key: " + response.data.ingest.key });
      clearInterval(poll_interval);
    } else {
      self.setState({ message: 'Polling' + '.'.repeat(1 + counter%3) });
    }
    counter = counter + 1;
  } catch (error) { console.log(error) }
}, 3000);
```

### Step 4. Building the broadcast page UI

We build a very simple user interface. The front page will have a drop-down menu to select the `region_value`. This drop-down contains the following regions \(you can find the available regions here: [Regions](https://starboy.gitbook.io/uiza-doc/getting-started/regions)\):

* in-bangalore-1
* in-mumbai-1

We create a `Start broadcast` button to call the `start_broadcast` function. The three lines below are important. They leverage the state value to display current states.

The first line displays the messages from the program's status: `Fetching`, `Polling` etc.

```javascript
{this.state.message}<br/>
```

The second line contains the stream URL \(i.e. `stream_url`\)

```javascript
{this.state.broadcast_url}<br/>
```

The third line contains the key for the stream key \(i.e `stream_key`\)

```javascript
{this.state.broadcast_key}<br/>
```

#### Putting the broadcast page UI together:

```javascript
render() {
    return (
      <div className='page'>
        <div className="App">
          <h1> Uiza Guide </h1>
          <header className="App-header">

            <div style={{ align: "left", float: 'left', width: "45%", margin: "10px", height: "220px", padding: '10px', border: "1px solid white" }}>
              <p> Start broadcast <br />
                <label>Pick your region: &nbsp;
                <select value={this.state.region_value} onChange={(event) => { this.setState({ region_value: event.target.value }); }}>
                    <option value="in-bangalore-1">in-bangalore-1</option>
                    <option value="in-mumbai-1">in-mumbai-1</option>
                  </select>
                </label> &nbsp;
              <button onClick={this.start_broadcast}>Start broadcast</button> <br />
              {this.state.message}<br/>
              {this.state.broadcast_url}<br/>
              {this.state.broadcast_key}<br/>
              </p>
            </div>
            </header>
        </div></div>
    )
  }
}

export default App;
```

### Step 5. Building the View Page

The view page contains tiles that correspond to available streams. Green tiles are online entities and red tiles are offline entities.

The following `load_alive_streams` function loads the streams. Available streams are loaded and saved to `state` so that they update automatically.

```javascript
load_alive_streams = async () => {
    var options = {
      "method": "get",
      "url": url,
      "headers": {
        "Content-Type": "application/json"
      }
    };
    var response = await axios(options);
    var data = response.data.data;
    var streams = [];
    data.forEach(element => {
      try {
        streams.push({
          online: element.broadcast === 'online' ? true : false,
          stream_url: element.ingest.url,
          stream_key: element.ingest.key,
          playback_url: element.playback.hls
        })
      } catch (err) { }
    });
    this.setState({
      streams: streams,
      last_loaded: new Date()
    });
    console.log(`Completed reading data: ${streams.length} streams are online now!`);
  }
```

#### Rendering the view page UI

We create a dynamic list of VideoTiles, and populate it on every render\(\). We use a 5-second interval between each render, to not overdo it. Then we access the details from the properties of the Video at the time of creation. We use the properties to pass values to the inner components of the tile and make it look functional.

For example: `{this.props._url}` accesses the `_url` parameter from `<VideoTile>` The same approach is used for the key and the playback URL.

The tile has to be clickable and take the viewer to the live stream. For that, we make use of routing in our application and send the user to a page with video playback url. The playback page is dynamically generated and plays the video.

```javascript
<a href={"./video/" + this.props._playback_url.replace(/(^\w+:|^)\/\//, '')}>
```

The above line sends the user to an `href` link which is understood by the router later. The regex removes the protocol from the URL \(i.e http / https\)

Following code shows the VideoTile component:

```javascript
class VideoTile extends Component {

  render() {
    return (
      <div style={{
        width: "240px", height: "200px", float: "left", margin: "10px", padding: "8px", display: "flex", flexDirection: "column",
        wordWrap: "break-word", fontSize: "16px", border: "2px solid white", backgroundColor: this.props._online ? 'MediumSeaGreen' : 'Tomato'
      }}>

        {/* remove http(s) */}
        <a href={"./video/" + this.props._playback_url.replace(/(^\w+:|^)\/\//, '')}>
          <span name='url'>URL: {this.props._url}</span><br /><br />
          <span name='key'>KEY: {this.props._key}</span><br /><br />
          <span name='playback_url'>PLAYBACK: {this.props._playback_url}</span>
        </a>
      </div>
    )
  }
}
```

As mentioned above, requests are only made every 5-seconds. We attach the parameters to the VideoTile element. After putting it all together:

```javascript
render() {
    try {

      if (typeof this.state.last_loaded === "string" || ((new Date() - this.state.last_loaded) / 1000) > 5) {
        var items = [];
        this.load_alive_streams().then((result) => {

          for (const [index, value] of this.state.streams.entries()) {
            items.push(<VideoTile key={index}
                                  _url={value.stream_url}
                                  _key={value.stream_key}
                                  _playback_url={value.playback_url}
                                  _online={value.online}></VideoTile>)
          }

          this.setState({ items: items });
          console.log('Loading complete');
        });
      }
    } catch (err) {
      this.setState({ last_loaded: new Date() });
    }

    return (
      <div className="App">
        <h1 style={{ padding: "8px" }}>  Uiza Online Videos </h1>
        <header className="App-header">
          <div name='tileContainer'>
            {this.state.items}
          </div></header>
      </div>
    )
  }
```

### Step 6. Playback the live stream

Now we have the video tiles ready but what do we show when this tile is clicked? This clever little view code launches the player on screen. We launched the player on the screen when the tile is clicked with the following code:

```javascript
function VideoPage() {
  let { videoid } = useParams();
  return (
    <div style={{ padding: "20px" }}>
      <ReactPlayer url={"https://" + videoid} playing={true} controls={true}></ReactPlayer>
    </div>)
}
```

#### Routing and APP overall UI

We make use of the `Router` component in react to create pagination in our app. We will have the link to broadcast and view page

To enable pagination in the app, we need to make use of react's routing. Following code does the routing:

```javascript
class App extends Component {

  render() {
    return (
      <Router>
        <div className='page'>
          <nav>
            <ul>
              <li>
                <Link to="/broadcast">Broadcast Page</Link>
              </li>
              <li>
                <Link to="/viewer" onClick={ViewerPage.load_alive_streams}>Viewer Page</Link>
              </li>
            </ul>
          </nav>

          {/* A <Switch> looks through its children <Route>s and
          renders the first one that matches the current URL. */}
          <Switch>
            <Route path="/broadcast">
              <BroadcastPage />
            </Route>
            <Route path="/viewer">
              <ViewerPage />
            </Route>
            <Route path="/video/:videoid*">
              <VideoPage />
            </Route>
          </Switch>
        </div>
      </Router>
    )
  }
}
```

The streams are loaded when we click on the viewer with the below line. Following line loads the streams on click: `<Link to="/viewer" onClick={ViewerPage.load_alive_streams}>Viewer Page</Link>`

The routing path below with `*` wildcard enables video stream url to be parsed with `/` and to be sent to the video page. Otherwise, the videoid is split at the first occurence of `/`

```javascript
<Route path="/video/:videoid*">
              <VideoPage />
```

## Conclusion

That's all wasn't that fun? If you have any questions please check out our Github repo where this entire project has been uploaded with the Java source code [here](https://github.com/uizaio/uiza-live-java-server-integration) and the Javascript source code [here](https://github.com/uizaio/uiza-node-sample-app). If you have any other questions please contact us here: [anhnh@uiza.io](mailto:anhnh@uiza.io)

