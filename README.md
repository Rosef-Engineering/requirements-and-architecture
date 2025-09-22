[<sub>Copyright Rosef Engineering 2024</sub>](/reuse/dep5)  
  
<a href="https://rosef.rs/"><img src="https://github.com/Rosef-Engineering/.github/raw/main/profile/logo.jpg" alt="Rosef" width="300"/></a>  
  
  
## Let's Electrify Africa 
   

This repository is a part of Rosef's efforts at developing <!-- The goal of Rosef is to develop // This project is a part of Rosef's efforts at developing -->a sustainable solution for electrification, with the main focus being on Africa. More specifically, our target is to start with homes and small businesses in Africa. Owing to the weather conditions in the majority of our target region, solar (photovoltaic) power is the basis of our solution.  
  
Stemming from our goal of minimizing system cost without making compromises, the three key technical concepts of our approach are:  
- **Use of direct energy storage methods**  
Lowering the dependency of renewables on lithium batteries which are expensive and have limited sustainability.  
- **Moving towards the DC future**  
Removing redundant AC/DC conversion and the associated power losses and investment costs.  
- **Smart and seamless resource managment**  
Avoiding compromises without oversizing the system by enable communication between nodes in the system.  
  
<!-- For more information about the background of these points, please see:  
1. [<img src="https://github.com/Rosef-Engineering/.github/raw/main/profile/youtube-color-icon.png" alt="YouTube" width="20"/>Let's Electrify Africa Together](https://youtu.be/rNMp0fn0p1k)
2. [<img src="https://github.com/Rosef-Engineering/.github/raw/main/profile/youtube-color-icon.png" alt="YouTube" width="20"/>Our Vision for the Electrification of Africa](https://www.youtube.com/@RosefOfficial) (coming soon). 
Icon source: https://uxwing.com/youtube-color-icon/ -->  
   

## Licensing
  
Most of the contents of this repository and licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by/4.0/). See the [LICENCE](/LICENCE.txt) file for the legal code. See [this](/reuse/dep5) file for file-specific information.  


## Goals and Architecture
Due to the scope of Rosef's goals, it is necessary to define priorities in order to focus efforts and achieve targets. This prioritization should be done based on required effort as well as importance of functionality for the end user. Based on these points, the following development stages have been defined. The initial stages all exclusively use extra low voltage (ELV), in order to minimize costs and development effort while ensuring safety.

It should be noted that these stages are simply a reflection of the current plan and are flexible both in terms of overlap as well as complete restructuring according to the above stated prioritization parameters as well as the available knowledge base of the contributors.

### Stage I - Lighting, Charging and Motor Drive
For the first goals, functionality such as __interior lighting__ and __personal device charging__ (phone, laptop, etc.), may seem like clear choices, due to the ease of implementation as well as usefulness to the end user.
However, given the economic situation of the vast majority of the target demographic, it cannot be ignored that the aforementioned functionality can be viewed merely as a cheaper (and more convenient) solution to the existing alternative (gas lamps and charging as a service).
With low usage, the cost effectiveness of the solution would rely on spreading the investment costs far into the future, which would make the sourcing of investment funds difficult. 
Thus, focusing on productive uses of electricity, which could create a lot of economic opportunity, seems like the better choice.
A robust, repairable and reliable __generic motor drive__, which could easily be adapted to a variety of productive applications, could prove to be useful.
<!--That being said, __interior lighting__ is helpful for productive use cases as much as for domestic ones.-->

<figure>
  <img src="https://raw.githubusercontent.com/Rosef-Engineering/requirements-and-architecture/main/export-svg/stage1.svg" alt="Stage I Block Diagram" width="900"/>
  <figcaption>Figure: Stage I Block Diagram</figcaption>
</figure>  
<br/><br/>

As shown in the resulting block diagram in the figure above, the components which need to be developed in order to achieve this stage include:

* __Battery Mini__ - a modular electrical energy storage unit interfaced to the nano-grid through a bidirectional converter
* __PV Mini__ - an MPPT converter for interfacing a photovoltaic solar panel to the nano-grid
* __ELV Meter__ - an energy consumption measurement unit relaying relevant information via the communication lines
* __ELV Socket__ - electronics for interfacing devices to the nano-grid and enabling smart managment of limited resources
* __USB Charger__ - a USB PD charger for personal devices including phones, laptops, etc.
* __Generic Motor Drive__ - a motor drive adaptable to a variety of productive use applications

### Stage II - Water, Food Storage and Community Lighting

The goal of this stage is to implement direct energy storage systems and in doing so solve two topics which are important in many rural areas in Africa. In short, the two topics are the question of __water supply__ and of __food storage__.

<figure>
  <img src="https://raw.githubusercontent.com/Rosef-Engineering/requirements-and-architecture/main/export-svg/stage2.svg" alt="Stage II Block Diagram" width="900"/>
  <figcaption>Figure: Stage II Block Diagram</figcaption>
</figure>  
<br/><br/>

As shown in the resulting block diagram in the figure above, the components which need to be developed in order to achieve this stage include:

* __Water Well System__ - a water well and tower system which helps efficiently manage electricity usage
* __Ice Thermal Storage Refrigerator__ - a refrigerator with a compartment with water which can be frozen and used for refrigerating the food later

### Stage III - Low Power Kitchen

Another challenging question for rural and unelectrified areas is __clean cooking__. This is a topic which cannot be fully covered with the power limitations of an ELV system ([see Dual Concept below](https://github.com/Rosef-Engineering/.github/blob/main/_chapters/goals-stages.md#dual-concept)), but some kitchen appliances do not require high power and those are the target of this stage.

<figure>
  <img src="https://raw.githubusercontent.com/Rosef-Engineering/requirements-and-architecture/main/export-svg/stage3.svg" alt="Stage III Block Diagram" width="900"/>
  <figcaption>Figure: Stage III Block Diagram</figcaption>
</figure>  
<br/><br/>
  
As shown in the resulting block diagram in the figure above, the components which need to be developed in order to achieve this stage include:

* __Microwave Oven__ - adapted so that it can be supplied from an ELV line
* __Rice Cooker__ - adapted so that it can be supplied from an ELV line

### Dual Concept
As mentioned above, the initial stages all exclusively use ELV due to the safety benefits it brings without increasing costs or required development effort. That being said, transfering a significant amount of power over such a low voltage quickly becomes impractical because of the amperage which would be necessary. If the current is limited to 16A, a 48V line can only transfer 768W. In contrast, with 230V, 16A yields 3680W and, for example, 340V&#xB7;16A=5440W. DC voltages above 120V, however, have significant safety implications which need to be adressed properly, so they should be used only where high power is a requirement. To address such needs, the dual voltage concept shown in the figure below has been defined. More detailed stages will be defined once more progress has been made with the initial stages.

<figure>
  <img src="https://raw.githubusercontent.com/Rosef-Engineering/requirements-and-architecture/main/export-svg/dual_concept.svg" alt="Dual Concept Block Diagram" width="750"/>
  <figcaption>Figure: Dual Concept Block Diagram</figcaption>
</figure>  
<br/><br/>

  

## Repository Content

The goal of this repository and its contents is to document the design of the system and its components in order to enable technical discussions and development coordination. In the long term, the target is to have detailed requirements and architecture, assuring traceability and consistency throughout the development process.  
Currently, the block diagrams are created in [Ipe](https://ipe.otfried.org/), exported in svg format and combined with markdown text. In addition, some parts, which are best suited for tabular representation, are in the form of spreadsheets.  
1.  [System architecture]()<!-- TODO -->  
2.  [ELV Socket architecture]()<!-- TODO -->  


## How to Contribute
  
If you believe that you have a skill that could be useful to Rosef's efforts and would like to contribute, consider joining our [Discord community](https://discord.gg/ryhPa73Cs3) and introducing yourself there.

To get started, please follow these steps:  
1. Understand the system architecture described in the [Requirements and Architecture repository](https://github.com/Rosef-Engineering/requirements-and-architecture).  
2. Go through the [list of repositories](https://github.com/Rosef-Engineering#repositories-and-project-status) and see which parts of the project are open for contributions. Select one.  
3. Find the selected component in [this list](https://github.com/Rosef-Engineering/requirements-and-architecture#repository-content) and understand its architecture.  
4. Fork the project to your personal github profile.  
5. Clone the forked repo and implement the contributions you would like to submit.  
6. Take care to follow any licence related rules relevant for that repo.  
7. Push your changes and submit a change request. <!-- TODO Decision: leave room for change of licence? -->  
 


## More About Us

You can learn more about us and follow our progress on our [Main YouTube channel](https://youtube.com/@RosefOfficial/).
For more technically focused updates, check out our other channel [Rosef Engineering](https://youtube.com/@RosefEngineering/).
If you wish to support us financially, please use one of the following options:

* [Buy Me a Coffee](https://buymeacoffee.com/rosefofficial)

* [Patreon](https://patreon.com/Rosef)

* [SubscribeStar](https://www.subscribestar.com/rosef)
 

