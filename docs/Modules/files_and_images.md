# Files &amp; Images

Quarx is always concerned with security of what you provide, the potential open doors in your website/ app. As such, the Files and Images which are uploaded to Quarx are locked outside of the public access points.

*What does this mean?*

This means that when you're website is providing these to visitors they are actually getting them through an API access point. This is done to ensure that the files do not reveal thier location. This means that no webscrappers can crawl your directories and take off with images, or files they shouldnt be, including files and images that have yet to be released.

# Storage Location

In the config you can set the storage location for your file and image uploads. This can be either S3 or local. To get S3 to work correctly you need to configure Laravel as you would with S3. Quarx will take it from there. So simply add your details to the config and it should work. Quarx loads all the third-party packages you will need.
