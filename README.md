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

    html.push('<a href="' + profi le_url + '"><img src="' +  portrait_large + '" alt=""></a>');
    html.push('<div><h3>' + display_name + '</h3>');
    html.push('<h4><a href="' + profile_url + '">' + profile_url + '</a></h4>');
    html.push('<ul><li><b>Videos: </b>' + total_videos_uploaded + '</li>');
    html.push('<li><b>Contacts: </b>' +  total_contacts + '</li>');
    html.push('<li><b>Channels: </b>' + total_channels + '</li>');
    html.push('<li><b>Likes: </b>' +  total_videos_liked + '</li></ul></div>');

    $('#userInfo').html(html.join(''));
                });    
```

### Get Group data
$.jvimeo.request(groupname, callback)

**Parameters**
* > request ("getActivityByUser").
* > groupname url or id string/int.
* > callback FUNC Function to call once the request has completed successfully. One parameter will be passed containing the JSON response of the request; callback(data).

**Requests you can make**
<table border="0" bordercolor="#FFCC00" style="background-color:#f8f8f8" width="100%" cellpadding="3" cellspacing="3">
	<tr>
		<td>getGroupVideos</td>
		<td>Videos added to that group</td>
	</tr>
	<tr>
		<td>getGroupUsers</td>
		<td>Users who have joined the group</td>
	</tr>
	<tr>
		<td>getGroupInfo</td>
		<td>Group info for the specified group</td>
	</tr>
</table>

**Example**
```
 $.jvimeo.getGroupVideos("2279524", function(data){
    var html = [];

    $.each(data, function (i, data) {
        html.push('<li>');
        html.push('<div class="details"><h3>' + data.title + '</h3>');
        html.push('<h4>by <a href="' + data.user_url + '">' + data.user_name + '</a></h4></div>');
        html.push('<a href="' + data.url + '" target="_blank" class="linkc">');
        html.push('<img src="' + data.thumbnail_large + '" alt="' + data.title + '">');
        html.push('</a></li>');
    });
    
    $('#shotsListing').html(html.join(''));
                });     
```

### Get Channel data
$.jvimeo.request(channelname, callback)

**Parameters**
* > request ("getChannelVideos").
* > channelname url or id string/int.
* > callback FUNC Function to call once the request has completed successfully. One parameter will be passed containing the JSON response of the request; callback(data).

**Requests you can make**
<table border="0" bordercolor="#FFCC00" style="background-color:#f8f8f8" width="100%" cellpadding="3" cellspacing="3">
	<tr>
		<td>getChannelVideos</td>
		<td>Videos in the channel</td>
	</tr>
	<tr>
		<td>getChannelInfo</td>
		<td>Channel info for the specified channel</td>
	</tr>
</table>

**Example**
```
 $.jvimeo.getChannelVideos("2279524", function(data){
    var html = [];

    $.each(data, function (i, data) {
        html.push('<li>');
        html.push('<div class="details"><h3>' + data.title + '</h3>');
        html.push('<h4>by <a href="' + data.user_url + '">' + data.user_name + '</a></h4></div>');
        html.push('<a href="' + data.url + '" target="_blank" class="linkc">');
        html.push('<img src="' + data.thumbnail_large + '" alt="' + data.title + '">');
        html.push('</a></li>');
    });
    
    $('#videos').html(html.join(''));
                });     
```

### Get Album data
$.jvimeo.request(Albumname, callback)

**Parameters**
* > request ("getChannelVideos").
* > Albumname url or id string/int.
* > callback FUNC Function to call once the request has completed successfully. One parameter will be passed containing the JSON response of the request; callback(data).

**Requests you can make**
<table border="0" bordercolor="#FFCC00" style="background-color:#f8f8f8" width="100%" cellpadding="3" cellspacing="3">
	<tr>
		<td>getAlbumVideos</td>
		<td>Videos in that album</td>
	</tr>
	<tr>
		<td>getAlbumInfo</td>
		<td>Album info for the specified album</td>
	</tr>
</table>

**Example**
```
 $.jvimeo.getAlbumVideos("2279524", function(data){
    var html = [];

    $.each(data, function (i, data) {
        html.push('<li>');
        html.push('<div class="details"><h3>' + data.title + '</h3>');
        html.push('<h4>by <a href="' + data.user_url + '">' + data.user_name + '</a></h4></div>');
        html.push('<a href="' + data.url + '" target="_blank" class="linkc">');
        html.push('<img src="' + data.thumbnail_large + '" alt="' + data.title + '">');
        html.push('</a></li>');
    });
    
    $('#videos').html(html.join(''));
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
		<td>upload_date</td>
		<td>The date/time the video was uploaded on</td>
	</tr>
	<tr>
		<td>user_portrait_small</td>
		<td>Small user portrait (30px)</td>
	</tr>
	<tr>
		<td>user_portrait_medium</td>
		<td>Medium user portrait (100px)</td>
	</tr>
	<tr>
		<td>user_portrait_large</td>
		<td>Large user portrait (300px)</td>
	</tr>
	<tr>
		<td>stats_number_of_likes</td>
		<td># of likes</td>
	</tr>
	<tr>
		<td>stats_number_of_views</td>
		<td># of views</td>
	</tr>
	<tr>
		<td>stats_number_of_comments</td>
		<td># of comments</td>
	</tr>
	<tr>
	duration</td>	<td>Duration of the video in seconds</td></tr>
<tr>
<td>width</td>	<td>Standard definition width of the video</td></tr>
<tr>
<td>height</td>	<td>Standard definition height of the video</td></tr>
<tr>
<td>tags</td>	<td>Comma separated list of tags</td></tr>
</table>

**User info data**
<table border="0" bordercolor="#FFCC00" style="background-color:#f8f8f8" width="100%" cellpadding="3" cellspacing="3"><tr>
                    <td>id</td>
                    <td>User ID</td>
                </tr>
                <tr>
                    <td>display_name</td>
                    <td>User name</td>
                </tr>
                <tr>
                    <td>created_on</td>
                    <td>Date the user signed up</td>
                </tr>
                <tr>
                    <td>is_staff</td>
                    <td>Is this user a staff member?</td>
                </tr>
                <tr>
                    <td>is_plus</td>
                    <td>Is this user a Vimeo Plus member?</td>
                </tr>
                <tr>
                    <td>location</td>
                    <td>The location of the user</td>
                </tr>
                <tr>
                    <td>url</td>
                    <td>User supplied url</td>
                </tr>
                <tr>
                    <td>bio</td>
                    <td>The bio information from the user profile</td>
                </tr>
                <tr>
                    <td>profile_url</td>
                    <td>URL to the user profile</td>
                </tr>
                <tr>
                    <td>videos_url</td>
                    <td>URL to the video list for this user</td>
                </tr>
                <tr>
                    <td>total_videos_uploaded</td>
                    <td>Total # of videos uploaded</td>
                </tr>
                <tr>
                    <td>total_videos_appears_in</td>
                    <td>Total # of videos user appears in</td>
                </tr>
                <tr>
                    <td>total_videos_liked</td>
                    <td>Total # of videos liked by user</td>
                </tr>
                <tr>
                    <td>total_contacts</td>
                    <td>Total # of contacts</td>
                </tr>
                <tr>
                    <td>total_albums</td>
                    <td>Total # of albums</td>
                </tr>
                <tr>
                    <td>total_channels</td>
                    <td>Total # of channels moderated by user</td>
                </tr>
                <tr>
                    <td>portrait_small</td>
                    <td>Small user portrait (30px)</td>
                </tr>
                <tr>
                    <td>portrait_medium</td>
                    <td>Medium user portrait (100px)</td>
                </tr>
                <tr>
                    <td>portrait_large</td>
                    <td>Large user portrait (300px)</td>
                </tr>
            </table>

**Group info data**
<table border="0" bordercolor="#FFCC00" style="background-color:#f8f8f8" width="100%" cellpadding="3" cellspacing="3">
                <tr>
                    <td>id</td>
                    <td>Group ID</td>
                </tr>
                <tr>
                    <td>name</td>
                    <td>Group name</td>
                </tr>
                <tr>
                    <td>description</td>
                    <td>Group description</td>
                </tr>
                <tr>
                    <td>url</td>
                    <td>URL for the group page</td>
                </tr>
                <tr>
                    <td>logo</td>
                    <td>Group logo (header)</td>
                </tr>
                <tr>
                    <td>thumbnail</td>
                    <td>Thumbnail</td>
                </tr>
                <tr>
                    <td>created_on</td>
                    <td>Date the group was created</td>
                </tr>
                <tr>
                    <td>creator_id</td>
                    <td>User ID of the group creator</td>
                </tr>
                <tr>
                    <td>creator_display_name</td>
                    <td>Name of the User who created the group</td>
                </tr>
                <tr>
                    <td>creator_url</td>
                    <td>The URL to the group creator’s profile</td>
                </tr>
                <tr>
                    <td>total_members</td>
                    <td>Total # of users joined</td>
                </tr>
                <tr>
                    <td>total_videos</td>
                    <td>Total # of videos posted to the group</td>
                </tr>
                <tr>
                    <td>total_files</td>
                    <td>Total # of files uploaded to the group</td>
                </tr>
                <tr>
                    <td>total_forum_topics</td>
                    <td>Total # of forum topics</td>
                </tr>
                <tr>
                    <td>total_events</td>
                    <td>Total # of events</td>
                </tr>
                <tr>
                    <td>total_upcoming_events</td>
                    <td>Total # of upcoming events</td>
                </tr>
       </table>

**Channel info data**
<table border="0" bordercolor="#FFCC00" style="background-color:#f8f8f8" width="100%" cellpadding="3" cellspacing="3">
         <tr>
                    <td>id</td>
                    <td>Channel ID</td>
                </tr>
                <tr>
                    <td>name</td>
                    <td>Channel name</td>
                </tr>
                <tr>
                    <td>description</td>
                    <td>Channel description</td>
                </tr>
                <tr>
                    <td>logo</td>
                    <td>Channel logo (header)</td>
                </tr>
                <tr>
                    <td>url</td>
                    <td>URL for the channel page</td>
                </tr>
                <tr>
                    <td>rss</td>
                    <td>RSS feed for the channel’s videos</td>
                </tr>
                <tr>
                    <td>created_on</td>
                    <td>Date the channel was created</td>
                </tr>
                <tr>
                    <td>creator_id</td>
                    <td>User ID of the channel creator</td>
                </tr>
                <tr>
                    <td>creator_display_name</td>
                    <td>Name of the User who created the channel</td>
                </tr>
                <tr>
                    <td>creator_url</td>
                    <td>The URL to the channel creator’s profile</td>
                </tr>
                <tr>
                    <td>total_videos</td>
                    <td>Total # of videos posted in the channel</td>
                </tr>
                <tr>
                    <td>total_subscribers</td>
                    <td>Total # of users subscribed</td>
                </tr>
            </table>

**Album info data**
<table border="0" bordercolor="#FFCC00" style="background-color:#f8f8f8" width="100%" cellpadding="3" cellspacing="3">
                <tr>
                    <td>id</td>
                    <td>Album ID</td>
                </tr>
                <tr>
                    <td>created_on</td>
                    <td>Date the album was created</td>
                </tr>
                <tr>
                    <td>last_modified</td>
                    <td>Date the album was last modified</td>
                </tr>
                <tr>
                    <td>title</td>
                    <td>Album title</td>
                </tr>
                <tr>
                    <td>description</td>
                    <td>Album description</td>
                </tr>
                <tr>
                    <td>url</td>
                    <td>URL for the album page</td>
                </tr>
                <tr>
                    <td>thumbnail</td>
                    <td>Thumbnail</td>
                </tr>
                <tr>
                    <td>total_videos</td>
                    <td>Total # of videos added to the album</td>
                </tr>
                <tr>
                    <td>user_id</td>
                    <td>User ID of the user who made the album</td>
                </tr>
                <tr>
                    <td>user_display_name</td>
                    <td>Name of the User who created the album</td>
                </tr>
                <tr>
                    <td>user_url</td>
                    <td>The URL to the album creator’s profile</td>
                </tr>
            </table>
