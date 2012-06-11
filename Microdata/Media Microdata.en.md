# Media Microdata [English Version]

The primary purpose of the Media Microdata format is to let SnapPea's browser recognize when a block of HTML represents meta-data (contextual data) of a media file (text, picture, video, music). That way SnapPea can provide better contextual information to the user.

## Microdata format

SnapPea can handle the the following types of media:

* [Article](http://schema.org/Article)
	* [BlogPosting](http://schema.org/BlogPosting)
	* [NewsArticle](http://schema.org/NewsArticle)
	* [ScholarlyArticle](http://schema.org/ScholarlyArticle)
* [MediaObject](http://schema.org/MediaObject)
	* [AudioObject](http://schema.org/AudioObject)
	* [ImageObject](http://schema.org/ImageObject)
	* [MusicVideoObject](http://schema.org/MusicVideoObject)
	* [VideoObject](http://schema.org/VideoObject)

For Article and its derivatives, SnapPea will try to extract all text and make it available for download. For MediaObject and its derivatives, SnapPea will try to detect the link, and give this target to the user for download.

### Article

For Article and its derivatives, only the `articleBody` property is required, other properties are optional for SnapPea. 

	<div itemscope itemtype="http://schema.org/Article">
		<span itemprop="name">My speech</span>
		by <span itemprop="author">Cat Chen</span>
		<div itemprop="articleBody">
			<p>Blah blah blah...</p>
			<p>Blah blah blah...</p>
			<p>Blah blah blah...</p>
		</div>
	</div>

#### *\[itemprop=articleBody]

Body text of article.

### MediaObject

For MediaObject and its derivatives, only `contentUrl` is required,  other properties are optional for SnapPea. 

	<div itemscope itemtype="http://schema.org/AudioObject">
		<span itemprop="name">12oclock_girona.mp3</span>
		<script type="text/javascript">
			var fo = new FlashObject(
				"http://google.com/flash/preview-player.swf",
				"flashPlayer_719", "358", "16", "6", "#FFFFFF");
			fo.addVariable("url","http://media.freesound.org/"
				+ "data/0/previews/"
				+ "719__elmomo__12oclock_girona_preview.mp3");
			fo.addVariable("autostart", "0");
			fo.write("flashcontent_719");
		</script>
		<meta itemprop="encodingFormat" content="mp3" />
		<meta itemprop="contentURL"
			content="http://media.freesound.org/data/0/previews/719__elmomo__12oclock_girona_preview.mp3" />
		<span class="description">
			<meta itemprop="duration" content="T0M15S" />
			<span itemprop="description">Recorded on a terrace of Girona a sunday morning</span>
		</span>
	</div>

#### *\[itemprop=contentUrl]

Download URL (or broadcast URL) for the media file. 

### Other

Adding other properties will let SnapPea display richer data. The above-mentioned types can be embedded into other types. For example, if VideoObject is embedded in Movie, SnapPea will use the Movie type to get richer data about VideoObject. 

SnapPea supports the following types and data:

#### *\[itemprop=name]

Name of the media file, applies to all types of media.

#### *\[itemprop=contentSize]

Size of the media file for download, applies to MediaObject and its derivatives.

#### *\[itemprop=encodingFormat]

Encoding format of the media file, applies to MediaObject and its derivatives.

#### *\[itemprop=image]

URL of thumbnail image, applies to all types of media.

#### *\[itemprop=thumbnailUrl]

URL of thumbnail image, applies to all types of media.

#### *\[itemprop=thumbnail]

The target for a thumbnail, applies to ImageObject and VideoObject. SnapPea will only read the included `*\[itemprop=image]` property.  

#### *\[itemprop=byArtist]

Artist name, applies to all encodings, including MediaObject and its derivative MusicRecording. 

