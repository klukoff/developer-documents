# App Microdata [English Version]

## description

The purpose of app microdata is to let SnapPea and other search engines know that a block of HTML description is an app. When a user wants to download or update an app, the service can provide the name, version, icon, description and other data. The uses of this include:

*To provide data for the "1-click download" feature
*To let search spiders recognize the data

## Microdata format

	<div itemscope itemtype="http://schema.org/SoftwareApplication" class="download">
		<img itemprop="image" src="https://ssl.gstatic.com/android/market/com.zeptolab.ctr.paid/hi-124-11" />
		<a itemprop="url" href="">
			<span itemprop="name">Cut the Rope</span>
			(<span itemprop="softwareVersion">1.3</span>)
		</a>
		<div itemprop="description">Cut the Rope, catch a star, and feed Om Nom candy in this award-winning game! The long-awaited hit game has finally arrived at Android!</div>
		<a itemprop="downloadURL" href="">Download</a> (<span itemprop="fileSize">18,123,456</span>)
	</div>

All app-related operations use a `*[itemscope]` tag, which includes a `class` property and an `*[itemprop]` element.

### class

If `class` includes `snp-app-download` type, the SnapPea client will use `packageName` and `softwareVersion` to check if the user already has a previous version of the app installed. If yes, then `snp-app-download` will be updated to `snp-app-update` (update available) or `snp-app-downloaded` (already download)

### *\[itemprop=name]

The app name displayed to the user.

### *\[itemprop=packageName]

Name of the app package.

### *\[itemprop=softwareVersion]

App version number.

### *\[itemprop=fileMd5]

App APK file's md5 data.

### *\[itemprop=url]

URL of the page with the app's detailed info.

### *\[itemprop=downloadUrl]

Download URL for the app's APK file 

### *\[itemprop=description]

The app description displayed to the user.

### *\[itemprop=image]

The app icon displayed to the user.

### *\[itemprop=fileSize]

Size of the app's APK file, provided in number of bytes.

### *\[applicationCategory]

App category.

### Other

Aside from the above-mentioned properties, please consult the following document for additional custom properties [Schema.org Documentation](http://schema.org/SoftwareApplication).
