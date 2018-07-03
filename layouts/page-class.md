[nav]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/page-class/navbarpage.png "Zebble-Stack"
[sample]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/page-class/samplemarkup.png "Zebble-Stack"
[output]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/layouts/page-class/output.png "Zebble-Stack"

### PAGE CLASS

Page is a sub-class of View and its role is to represent one whole screen on the mobile device. Its primary functionality is to facilitate navigation from one page to another using the **Nav** class.

![nav]


Master pages in M# are represented as a sub-class of the Page class. For example the default new project template comes with a template named **PageWithNavBar** which inherits from **Zebble.Page** and adds the tabs and nav bar at the top of it to be reused in all page classes that inherit from it.

In summary, we use inheritance to reuse functionality (such as navigation bar and tabs) across several page classes.

For example, after successful compiling of below codes, we can see the output which is shown in second image.


**Sample Markup**
 

![sample]


The Output page is:


![output]