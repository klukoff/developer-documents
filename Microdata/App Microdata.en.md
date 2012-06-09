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

直接展示给用户看的应用名称。

### *\[itemprop=packageName]

应用包名称。

### *\[itemprop=softwareVersion]

应用版本号。

### *\[itemprop=fileMd5]

应用 apk 文件的 md5 摘要信息。

### *\[itemprop=url]

应用详情页地址。

### *\[itemprop=downloadUrl]

应用 apk 文件下载地址。

### *\[itemprop=description]

直接展示给用户看的应用描述。

### *\[itemprop=image]

直接展示给用户看的应用图标。

### *\[itemprop=fileSize]

应用 apk 文件体积，用按字节计算的整数表示。

### *\[applicationCategory]

应用类别。

### 其他

除去上述必要的属性外，其它自定义属性可以参考 [Schema.org 的文档](http://schema.org/SoftwareApplication)。
