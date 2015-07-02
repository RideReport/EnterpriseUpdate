# EnterpriseUpdate
Simple in-app updates for Enterprise App Distribution

# Setup
1. Set up a new bucket on S3 to contain your app beta. Make a new access key configured with write access to this bucket.
2. Upload full (512x512) and display (57x57) pngs for your app icon. Make them public and make note of their urls.
3. Edit manifest.plist to include your app display name, company name, bundle idenitifer and the full-size-image and display-image urls you created in step 2.
4. Edit upload-iphone to include your app name and AWS bucketname and acess keys from step 1.
5. Copy SoftwareUpdateManager.swift to your iOS project.
6. Edit SoftwareUpdateManager.swift to include your bucketName and appName.
7. Somewhere during your application application didFinishLaunchingWithOptions, call:
`SoftwareUpdateManager.startup()`

# Uploading a build
1. Make sure you've incremented the bundle-version in your Info.plist file.
2. Archive the build and export it for enterprise to the directory containing upload-iphone and your edited manifest.plist file.
3. Run:
`ruby upload-iphone`
