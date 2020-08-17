# magento_test_task3
You need to -
1. Remove 2 random fields from the Shipping step;
2. All other field names, which should be written vice versa, like Name, should be emaN.
3. And the next step button should redirect back to the cart.

Please document all your changes for step 1. So we will know what was removed.

You can use any Magento 2 installation that you have.
Please also attach the documented installation process and the user with general explanations.
So we will be super sure to understand them correctly.

------------
Theme Installation 
------------

### 1. Using Zip File

* Download the Extension Zip File
* Extract & upload the files to /path/to/magento2/app/design/frontend/Baracat/base/

After installation by either means, enable the extension by running following commands (from root of Magento2 installation):

Then you should run Magento's setup upgrade:
```
php bin/magento setup:upgrade
```
Now you activate the Baracat/base Theme under `Content -> Design -> Configuration..`

![alt text](https://raw.githubusercontent.com/baracatuemura/magento_test_task3/master/_info/image1.png)

Lastly clear Magento generated suff and caches:
```
rm -rf pub/static/frontend/
rm -rf var/view_preprocessed/css/frontend/
php bin/magento cache:clean
```
------------
Solutions
------------

### 1. Remove 2 random fields from the Shipping step.

This task can be performed in two ways:

1. By Control Panel

Go to `Store -> Configuration -> Customer -> Customer Configuration..`
On tab `Name and Address Options` choose the options you want hide.

![alt text](https://raw.githubusercontent.com/baracatuemura/magento_test_task3/master/_info/image4.png)


2. By Layout XML file

Removed using checkout_index_index.xml file and add node below:

```
<item name="visible" xsi:type="boolean">false</item>
```
![alt text](https://raw.githubusercontent.com/baracatuemura/magento_test_task3/master/_info/image2.png)

### 2. All other field names, which should be written vice versa, like Name, should be emaN.

To make this item I used the theme translation file en_US.csv

![alt text](https://raw.githubusercontent.com/baracatuemura/magento_test_task3/master/_info/image3.png)


### 3. And the next step button should redirect back to the cart.

To make this item I overide core template coping the file into the created theme folder:
```
Magento_Checkout -> web -> template -> shipping.html
```

and changing the lines of code below:

```
<a class="button action continue primary viewcart" href="cart">
    <span translate="'Next'"/>
</a>
 ```
![alt text](https://raw.githubusercontent.com/baracatuemura/magento_test_task3/master/_info/image6.png)

------------
Screenshot of final result
------------
![alt text](https://raw.githubusercontent.com/baracatuemura/magento_test_task3/master/_info/image5.png)
