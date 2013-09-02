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
<table border="0" bordercolor="#FFCC00" style="background-color:#f8f8f8" width="100%" cellpadding="3" cellspacing="3">
	<tr>
		<td>getUserInfo</td>
		<td>User info for the specified user</td>
	</tr>
	<tr>
		<td>getUserVideos</td>
		<td>Videos created by user</td>
	</tr>
	<tr>
		<td>getUserLikes</td>
		<td>Videos the user likes</td>
	</tr>
	<tr>
		<td>getUserAppearsIn</td>
		<td>Videos that the user appears in</td>
	</tr>
	<tr>
		<td>getUserAllVideos</td>
		<td>Videos that the user appears in and created</td>
	</tr>
	<tr>
		<td>getUserSubscriptions</td>
		<td>Videos the user is subscribed to</td>
	</tr>
	<tr>
		<td>getUserAlbums</td>
		<td>Albums the user has created</td>
	</tr>
	<tr>
		<td>getUserChannels</td>
		<td>Channels the user has created and subscribed to</td>
	</tr>
	<tr>
		<td>getUserGroups</td>
		<td>Groups the user has created and joined</td>
	</tr>
</table>

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
$.jvimeo.getVideo(video_id, callback)

**Parameters**
* > video_id int.
* > callback FUNC Function to call once the request has completed successfully. One parameter will be passed containing the JSON response of the request; callback(data).

```
$.jvimeo.getVideo(161803, function(data){
    var html = [];

    $('#videoById a:first').attr('href', data.url);
    $('#videoById img').attr('src', data.thumbnail_large);
    $('#videoById h3').text(data.title);
    $('#videoById h4').html('by <a href="' + data.user_url + '">' + data.user_name + '</a>');

    html.push('<li><b>Views:</b> ' + data.stats_number_of_views + '</li>');
    html.push('<li><b>Likes:</b> ' + data.stats_number_of_likes + '</li>');
    html.push('<li><b>Comments:</b> ' + data.stats_number_of_comments + '</li>');

    $('#videoById ul').html(html.join(''));
                });    
```

### Get Activity data
$.jvimeo.request(username, callback)

**Parameters**
* > request ("getActivityByUser").
* > username or id string/int.
* > callback FUNC Function to call once the request has completed successfully. One parameter will be passed containing the JSON response of the request; callback(data).

**Requests you can make**
<table border="0" bordercolor="#FFCC00" style="background-color:#f8f8f8" width="100%" cellpadding="3" cellspacing="3">
	<tr>
		<td>getActivityByUser</td>
		<td>Activity by the user</td>
	</tr>
	<tr>
		<td>getActivityOnUser</td>
		<td>Activity on the user</td>
	</tr>
	<tr>
		<td>getActivityByContacts</td>
		<td>Activity by the user’s contacts</td>
	</tr>
	<tr>
		<td>getActivityEveryone</td>
		<td>Activity by everyone</td>
	</tr>
</table>

**Example**
```
$.jvimeo.getActivityByUser("IvanSotelo", function(data){
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

### Response Data.
There are a few different types of responses.

**Video data**
<table border="0" bordercolor="#FFCC00" style="background-color:#f8f8f8" width="100%" cellpadding="3" cellspacing="3">
	<tr>
		<td>title</td>
		<td>Video title</td>
	</tr>
	<tr>
		<td>url</td>
		<td>URL to the Video Page</td>
	</tr>
	<tr>
		<td>id</td>
		<td>Video ID</td>
	</tr>
	<tr>
		<td>description</td>
		<td>The description of the video</td>
	</tr>
	<tr>
		<td>thumbnail_small</td>
		<td>URL to a small version of the thumbnail</td>
	</tr>
	<tr>
		<td>thumbnail_medium</td>
		<td>URL to a medium version of the thumbnail</td>
	</tr>
	<tr>
		<td>thumbnail_large</td>
		<td>URL to a large version of the thumbnail</td>
	</tr>
	<tr>
		<td>user_name</td>
		<td>The user name of the video’s uploader</td>
	</tr>
	<tr>
		<td>user_url</td>
		<td>The URL to the user profile</td>
	</tr>
	<tr>
		<td>user_url</td>
		<td>The URL to the user profile</td>
	</tr>
</table>
