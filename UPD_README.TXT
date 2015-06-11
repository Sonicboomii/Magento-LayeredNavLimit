This repository is a modified version of Eyemagine's Magento-LayeredNavLimit in order to work on Magento CE
(only tested on version 1.9.1).

Since the plugin was designed for Magento Enterprise, I couldn't get the code to work as is or even when I moved it to my
local namespace. So, I edited filter.phtml and layerednavlimit.js and moved them to the appropriate folders. To get this
plugin to work (assuming you already have jQuery loaded), you must make the following changes:

DO NOT copy these folders:
app/etc/modules/
app/code/local/Eyemagine/LayeredNavLimit/
app/design/frontend/base/default/layout/eyemagine/

Move app/design/frontend/base/default/template/eyemagine/layerednavlimit/catalog/layer/filter.phtml -> 
app/design/frontend/[your theme]/template/catalog/layer/filter.phtml
You can also set the $_limit variable to the limit amount you want.

Copy the /skin/frontend/base/default/eyemagine/ folder to the same location

In app/design/frontend/[your theme]/layout/catalog.xml add the following under the <default> tag:
(If you don't already have catalog.xml, copy it from app/design/frontend/base/default/layout/catalog.xml)

<reference name="head">
    <action method="addItem"><type>skin_css</type><name>eyemagine/layerednavlimit/css/layerednavlimit.css</name></action>
     <action method="addJs"><script>eyemagine/layerednavlimit/js/layerednavlimit.js</script></action>
</reference>

Flush the Magento cache as well as the Javascript/CSS cache.
