##What is DCC++##

DCC++ is an open-source hardware and software system for the operation of DCC-equipped model railroads.

The system consists of multiple parts, the Hardware - [DCC++ Base Station](https://github.com/DccPlusPlus/BaseStation) and the Software - [DCC++ Controller](https://github.com/DccPlusPlus/Controller) or optionally [JMRI](http://www.jmri.org/).

The [DCC++ Base Station](https://github.com/DccPlusPlus/BaseStation) consists of an Arduino UNO or MEGA micro controller fitted with an [Arduino Motor Shield R3 or a Pololu Dual MC33926 Motor Shield](https://github.com/DccPlusPlus/Documentation/blob/master/Motor%20Shield%20Pin%20Mappings.pdf) that can be connected directly to the tracks of a model railroad.

The [DCC++ Controller](https://github.com/DccPlusPlus/Controller) provides operators with a customizable GUI to control their model railroad. It is written in Java using the [Processing graphics library and IDE](https://processing.org/) and communicates with the [DCC++ Base Station](https://github.com/DccPlusPlus/BaseStation) in one of multiple ways: Through a standard serial connection over a USB cable, wireless over BlueTooth, or with a Ethernet Shield via [JMRI](http://www.jmri.org/).

##What is a repository and what is in this Repository##

A repository is a central location in which data is stored and managed.  
We are using [GitHub](https://github.com/) as our repository.  

Inside [The DCC Plus Plus repository](https://github.com/DccPlusPlus?tab=repositories) you can find the following:  


- [Documentation](https://github.com/DccPlusPlus/Documentation) in the form of PDF files  
- [Base Station](https://github.com/DccPlusPlus/BaseStation) contains a complete DCC++ Base Station sketch designed for compiling and uploading into an Arduino Uno or Mega. All sketch files are in the folder named DCCpp_Uno. More information about the sketch can be found in the included [PDF file](https://github.com/DccPlusPlus/BaseStation/blob/master/DCC%2B%2B%20Arduino%20Sketch.pdf).  
- [Controller](https://github.com/DccPlusPlus/Controller) provides operators with a customizable GUI to control their model railroad.  
- [Track-Plans](https://github.com/DccPlusPlus/Track-Plans) This is the layout that is used to demonstrate the DCC++ system in various videos on [DCC++ YouTube channel](https://www.youtube.com/channel/UCJmvQx-fe0OMAIH-_g-_rZw) 

##Important References:##
  
- [This DCC Plus Plus repository](https://github.com/DccPlusPlus?tab=repositories)  
- [DCC++ YouTube channel](https://www.youtube.com/channel/UCJmvQx-fe0OMAIH-_g-_rZw)  
- [DCC++ Discussion on Trainboard](http://www.trainboard.com/highball/index.php?forums/dcc.177/)  
- [NMRA DCC Standards](http://www.nmra.org/index-nmra-standards-and-recommended-practices)  
- [Arduino](http://www.arduino.cc/)  
- [Processing](http://processing.org/)  
- [JMRI](http://www.jmri.org/)  
- [GNU General Public License](http://opensource.org/licenses/GPL-3.0)  


For more information on the overall DCC++ system, please follow the links in the [DCC++ WIKI](https://github.com/DccPlusPlus/BaseStation/wiki).  