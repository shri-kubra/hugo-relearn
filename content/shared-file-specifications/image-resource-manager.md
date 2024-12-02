---
title: "Image Resource Manager"
weight: 11
---

To standardize image links and quality on all platform products, KUBRA created a tool called Image Resource Manager (IRM).

IRM can be used to upload custom icons, brand images, social media images, and any other image assets that the client requires for any platform product. The tool allows for creating and archiving image resources that can then be used in Storm Center, IncidentWatch, or Notifi. Images uploaded using IRM will only be available for that specific client, and are automatically cached using CloudFront to avoid issues with website load during large events.

IRM supports the following image file types: JPEG, GIF, PNG, and SVG. The maximum file size allowed is 1 MB.

### System Default Preferences ###

While you can upload custom images that you might need in any product, KUBRA still maintains system default images that it recommends for use within its products.

To view these System Default Images, check the _Show System Default Preferences_ checkbox. These are KUBRA-created images and vectors that work best on our products.

### Image Properties ###

IRM asks for three parameters when uploading an image: the name, the image itself, and tags. The name and tags are modifiable if you want to edit them but the image cannot be changed. Any images that need to be changed will need the creation of a new IRM entry.

#### Image Tags ####

Tags help in searching and narrowing down specific images. They have a key-value pair association that can be created for that image. There is no limit on the number of tags you can associate with an image.

You can use the Search functionality to search by tags.

### Image Archive Functionality ###

You can archive an image already uploaded on IRM. Archiving exists to hide images that will not be used. Archived images are, however, still accessible by any product using them.

1. Click on the image you want to archive in the list of images. The image and its properties will open up on the right.
1. Click on the **Archive** button in the top right.

View Archived images by checking the _Show Archive_ checkbox.

{{% notice note %}}
Why do we not allow image deletion? In case any IRM image is being used within a product, deleting an image would cause the product to not function optimally. KUBRA wants to avoid that.
{{% /notice %}}

### Image Unarchive Functionality ###

You can unarchive images that have previously been archived. Click on the image you want to archive. On the right, click on the Un-Archive button.

### Sort By Functionality ###

The Sort By functionality allows you to sort by image name, either alphabetically or reverse alphabetically.

![Image Resource Manager with image/icon selected](/images/image-resource-manager-selected-image.jpg)

## Benefits of IRM ##

+ Simplifies adding and standardizing images.
+ Allows for platform products to be more customizable.
+ Creates path URLs to help reference images.
+ Caches images to allow for faster site load times.
+ Allows for images to be searched easily by allowing image tagging.

{{% notice note %}}
You can only reference path URLs from IRM in Storm Center 5 so far but image functionality will be extended to other platform products.
{{% /notice %}}

## Access IRM ##

1. Navigate to the Image Resource Manager website.
1. Sign in using Google or other single sign-on credentials.
1. Choose a tenant. This option is only presented if you have access to more than one tenant.
1. Choose Image Resource Manager.
