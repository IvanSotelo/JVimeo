JVimeo
======

A jQuery plugin to get information about public videos, users, groups, channels, albums, and activity from the Vimeo API. 
Visit www.deskode.com

## Dependencies
For normal usage; jQuery 1.3 or higher.

## Usage
JVimeo makes available methods for retrieving video and user information from the Vimeo.com API. All the available methods are accessed from the JVimeo object which is a member of the jQuery or $ object.

### Get User data
$.jvimeo.request(username, callback)

**Parameters**
* > request ("getUserInfo").
* > username or id string/int.
* > callback FUNC Function to call once the request has completed successfully. One parameter will be passed containing the JSON response of the request; callback(data).

**Requests you can make**

getUserInfo	          User info for the specified user
getUserVideos	        Videos created by user
getUserLikes        	Videos the user likes
getUserAppearsIn    	Videos that the user appears in
getUserAllVideos	    Videos that the user appears in and created
getUserSubscriptions	Videos the user is subscribed to
getUserAlbums       	Albums the user has created
getUserChannels	      Channels the user has created and subscribed to
getUserGroups	        Groups the user has created and joined

**Example**
```
$.jvimeo.getUserInfo("IvanSotelo", function(data){
    var html = [];

    html.push('<a href="' + profile_url + '"><img src="' +  portrait_large + '" alt=""></a>');
    html.push('<div><h3>' + display_name + '</h3>');
    html.push('<h4><a href="' + profile_url + '">' + profile_url + '</a></h4>');
    html.push('<ul><li><b>Videos: </b>' + total_videos_uploaded + '</li>');
    html.push('<li><b>Contacts: </b>' +  total_contacts + '</li>');
    html.push('<li><b>Channels: </b>' + total_channels + '</li>');
    html.push('<li><b>Likes: </b>' +  total_videos_liked + '</li></ul></div>');

    $('#userInfo').html(html.join(''));
                });    
```

### Get a Video data
$.jvimeo.resquest(username, callback)

**Parameters**
* > username string.
* > callback FUNC Function to call once the request has completed successfully. One parameter will be passed containing the JSON response of the request; callback(data).

