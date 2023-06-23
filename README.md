# CyL-base-stations-dataset

This excel file is composed by several sheets. They are the results of a preprocessing performed to the two sources of data explained below:

1. Population of Castilla y León in 2021 (https://www.ine.es/dynt3/inebase/index.htm?padre=1689&capsel=9041): This website has oficial data of the population of each spanish village. For our experiments we downloaded the data of all the villages of Castilla y León in 2021.
2. Location of Base stations in Spain (https://geoportal.minetur.gob.es/VCTEL/vcne.do ): This website shows the location of telecommunication antennas (base stations) in Spain. Given that the website only offers graphic results, a query using jq and a bash code was needed to get the data in .csv format.

After having the two above mentioned files, their data were combined to obtain the datased uploaded here. Below an explanation of each sheet of the file is offered:

1. PerVillage: This sheet is the first combination of the data from the two above mentioned sources. Each row is a village of Castilla y León, and for each of them we have the population, the province to which it belongs, the coordinates (latitude and longitude) of village's center. There is also a column with the number of antennas (BSs) in the village. Note that some villages have zero BSs.
2. WithoutAntenna: Given that according to the data, there are villages without BSs, what we did is assigning the population of these villages to the nearest BS. Then, this sheet contains all the villages without BSs, their population, their coordinates, and the name of the closest BS (the BSs are named with the name of their village, and if there are several BSs in a village a number is added).
3. NumberedAntennas: This sheet contains the data of the BSs. For each BS we have the coordinates, the name, the province to which it belongs, the local and total assigned population (remind that some villages have no BS, in such case its population is assigned to the nearest BS), a number to be used as identifier, and the angle and distance respect to the WAN gateway (Valladolid 1). The angle and distance values are used for the radial clustering. For the villages with several antennas, its population is equally distributed in each of the antennas.
4. AllDistances (1, 2 and 3): These three sheets contain the distance between each possible pair of BSs. Given that all these data in a single sheet is too long to be read by python, we split it into three parts.

All the sheets are included here to show where the data come from, and in case they are useful for another experiment. Nevertheless, in our simulations we only used 3 (NumberedAntennas), and 4 (AllDistances).
