                                                  HTA basic HOW-TO
WE all know that there are plenty of modern tools out there, but, for sure, wouldn't it be great to create a simple html file and just by changing it's filename extension from ".html" to ".hta" having a perfectly working application for all MS Windows systems!? 

Based on the principle of the least effort (https://en.wikipedia.org/wiki/Principle_of_least_effort), you may wish anytime in 
your life to create, REALLY FAST, a simple but yet robust working application with graphical user interface. Yes you can. Without Internet. Without Electron.  (But Only for MS Windows).

*********************************And yes, you can convert your code into Executable (.exe) ! (CHECK BELOW)

                                                             Documentation map :
                                                             1. Why HTA, instead of Electron or other ?
                                                             2. STOP TAKING BROADBAND CONNECTION AND TIME FOR GRANDED, EVERYWHERE
                                                             3. HTA NEEDED META TAGS : x-ua-compatible (super simple)
                                                             4. HTA NEEDED META TAGS : <HTA:APPLICATION> (optional)
      (BOILERPLATE TO INSTANT COPY - PASTE)   .>>>>>>>>>>    5. FINALY, GIMME SELTER (BOILERPLATE TO INSTANT COPY - PASTE)
                                                             6. Convert into Executable


**HTA stands for HTML Application and it was introduced as technology back in 1999.** 

\\// (Wikipedia)
An HTML Application (HTA) is a Microsoft Windows program whose source code consists of HTML, Dynamic HTML, and one or more 
scripting languages supported by Internet Explorer, such as VBScript or JScript. The HTML is used to generate the user interface, 
and the scripting language is used for the program logic.
[..] HTAs give the developer the features of HTML together with the advantages of scripting languages. They are popular with 
Microsoft system administrators who use them for system administration from prototypes to "full-scale" applications, especially 
where flexibility and speed of development are critical. (https://en.wikipedia.org/wiki/HTML_Application)
\\//

**-> HMMM... SO IT SOUNDS GREAT BUT WHY HTA, INSTEAD OF ELECTRON (OR VISUAL BASIC VIA MS VISUAL STUDIO, ETC.) ? (1)**

In fact, there are 2 known ways (to develop desktop apps fast and easily) : Electron, and HTA.
About Electron, the lazy way would be to go, here, on GitHub, at Electron/releases and download a stable release 
(right now 15-8-18, the best choice would be electron v2.0.7), depending on your system (Win/Mac/Linux). For a Windows
application you'd propably choose electron-v2.0.7-win32-x64.zip and then unzip at your projects folder. Under Electron's "/Resources" 
folder, create a folder named "app" and paste there your html file as "index.html". You may need to create a "manifest" and a "package" 
(package.json) file. See further, at https://electronjs.org/docs/tutorial/first-app.
Ofcourse this way would be better if you'd like to create a fully featured application. Thus, you'd be able to have an application working 
with other OS as Linux and MacOS. On the other hand, why mess with "manifests", downloading Electron files (~50mb) and wasting time 
at Electron documentations, for, let's say, an application that is showing plain messages with simple calculations ?

**--> STOP TAKING BROADBAND CONNECTION AND TIME FOR GRANDED, EVERYWHERE. (2)**

In my current job, we just needed an application that converts text input from Uppercase to Lowercase, 
just to change some products names. Thing is, that messing with Electron would had taken years, so I created a simple HTA application 
in seconds, *even without Internet connection to download the Electron files* !

**So, HTA is a real great tool to work with, even in ourdays!**

**-> HTA NEEDED META TAGS ********************************************************************************** (3)**
It's REALLY important to put the meta-tags below in your scripts, as higher as you can and before importing any library or calling any
 external script. X-ua-compatible, in case it's below anything else, it's just going to waste time, because when it's called it forces
 browser (internet explorer) to check again the code ! So remember : BASIC HTA META-TAGS ALWAYS ON TOP. ! :)
 1. x-ua-compatible 
  In order to work with todays browser standards you need to specify a modern IE version : 
  <meta http-equiv="x-ua-compatible" content="ie=EmulateIE11"/> for win7/later (best!)
  <meta http-equiv="x-ua-compatible" content="ie=EmulateIE9"/> for Vista,2008
  <meta http-equiv="x-ua-compatible" content="ie=EmulateIE8"/> for XP,2003
  <meta http-equiv="x-ua-compatible" content="ie=EmulateIE6"/> for NT 4.0, 98, 2000, ME
  <meta http-equiv="x-ua-compatible" content="ie=EmulateIE5"/> for Win95
  (for example, see boilerplate below)
  
2. <HTA:APPLICATION> ************************************************************************************** (4)
  example (first, see boilerplate below): <HEAD><HTA:APPLICATION ID="HelloExample" BORDER="thick" BORDERSTYLE="complex"/></HEAD>
  Accepted values :
*ApplicationName : Sets the name of the HTA. 
*Border : Sets the type of border used for the HTA window. 
 ->Values include: Thick. Creates a resizeable window. 
 ->Thin. Creates a window that cannot be resized. 
*BorderStyle : Sets the style of the content border in the HTA window. Values are: 
 ->Normal. Standard Windows border style. This is the default value. 
 ->Raised. Raised three-dimensional border. 
 ->Sunken. Sunken three-dimensional border. 
 ->Complex. Combines sunken and raised styles. 
 ->Static. Three-dimensional border typically used for windows that do not allow user input. 
*Caption : Yes/No value specifying whether the HTA displays a title bar. The default value is Yes. 
*Icon : Sets the path name of the icon that appears in the upper-left corner of the HTA window. 
  The icon can be either a .ico or a .bmp file. If not specified, a generic application icon is used. 
*ID : Sets the identifier for the <HTA:Application> tag. 
  This property is required if you need to write a script that returns the attributes of the HTA. 
*MaximizeButton : Yes/No value specifying whether the HTA displays a Maximize button in the title bar. The default value is Yes. 
*MinimizeButton : Yes/No value specifying whether the HTA displays a Minimize button in the title bar. The default value is Yes. 
*ShowInTaskbar : Yes/No value specifying whether the HTA is shown in the Windows taskbar. 
  Regardless of the value set for this property, the HTA will always appear in the list of applications that are accessible when you 
  press ALT+TAB. The default value is Yes. 
*SingleInstance : Yes/No value specifying whether more than one instance of this HTA can be active at any given time. 
  For this property to take effect, you must also specify the ApplicationName attribute. The default value is Yes. 
*SysMenu : Yes/No value specifying whether the HTA displays the System menu in the title bar. 
  The System menu is displayed in the upper-left corner of the HTA window and provides access to menu items such as Minimize, 
  Maximize, Restore, and Close. The default value is Yes. 
*WindowsState : Sets the initial size of the HTA window. Values are: Normal Minimize Maximize

**-> FINALY, GIMME SHELTER (BOILERPLATE) ********************************************************************** (5)**
*Minimal boilerplate (paste on notepad, do your tricks and save as .hta) : 
<!DOCTYPE html>
<html>
<head>
 <title>Application Title</title>
 <HTA:APPLICATION ID="ApplicationTitle" BORDER="thick" BORDERSTYLE="complex"/>
 <!-- // Needed metatag to work with IE. SUPER VERY IMPORTANT : -->
 <meta http-equiv="x-ua-compatible" content="ie=EmulateIE11"/>
 <!-- // Include Jquery, Bootstrap-->
 <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta/css/bootstrap.min.css">
 <script src="https://code.jquery.com/jquery-3.3.1.min.js" integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8=" crossorigin="anonymous"></script>
 <style>
   <!-- // CSS Style goes here-->
     <!-- // -->
   <!-- // CSS Style ends here-->
 </style>
</head>
<body>
  <!-- // HTML code goes here : -->
    <!-- // -->
  <!-- -->
  <script type="text/javascript">
    <!-- // JAVASCRIPT code goes here : -->
      <!-- // -->
    <!-- -->
    <!-- // JQUERY code goes here : -->
  </script>
  
  <script language="VBScript">
    'VBS code goes here
  </script>
  
  <!-- Window resizing and centering. It can also be inside the previous script area, it's just simple JS. -->
  <script type="text/javascript">
    function Window_onLoad(){  // resize to quarter of screen area, centered
	   //Custom resize - : 
         //window.resizeTo(300,290);
	   // - or resize depending on screen (very beautiful). :
         //window.resizeTo(screen.availWidth/2,screen.availHeight/2);
       //Centering :
         //window.moveTo(screen.availWidth/4,screen.availHeight/4);
    }
    window.onload=Window_onLoad;
  </script>
</body>
</html>

**-> Convert into executable**
It's highly suggested to download VBSedit and HTAedit. Just download VBSedit and HTAedit will be also installed. 
 (It's better to go and get them from their official trusted source, here : https://www.vbsedit.com).
Then on HTAedit paste your code and go to "File" > "Convert Into Executable". First you'll asked where to save the .hta file 
 and then about the .exe file. It's really easy. Go ahead, check it ! Now !
