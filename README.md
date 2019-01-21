# Chooser

## Overview

Forked from cyph/cordova-plugin-chooser.
Some problems with MIME type filter and Google Drive, so this plugin does not offer the possibility to filter by MIME type …

File chooser plugin for Cordova.

Install with Cordova CLI:

	$ cordova plugin add cordova-plugin-chooser

Supported Platforms:

* Android

* iOS

## API

	/**
	 * Displays native prompt for user to select a file.
	 *
	 * @returns Promise containing selected file's raw binary data,
	 * base64-encoded data: URI, MIME type, display name, and original URI.
	 *
	 * If user cancels, promise will be resolved as undefined.
	 * If error occurs, promise will be rejected.
	 */
	chooser.getFile() : Promise<undefined|{
		data: Uint8Array;
		dataURI: string;
		mediaType: string;
		name: string;
		uri: string;
	}>

## Example Usage

	(async () => {
		const file = await chooser.getFile();
		console.log(file ? file.name : 'canceled');
	})();


## Platform-Specific Notes

The following must be added to config.xml to prevent crashing when selecting large files
on Android:

```
<platform name="android">
	<edit-config
		file="app/src/main/AndroidManifest.xml"
		mode="merge"
		target="/manifest/application"
	>
		<application android:largeHeap="true" />
	</edit-config>
</platform>
```
