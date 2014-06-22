Merge-files
===========
### subject of alll obsevation is in the next file, then put all information in one file
t1_sub <-read.table("./UCI HAR Dataset/train/subject_train.txt")
t1_sub$ID <- seq(1,7352, by=1)
## read packages
library(plyr)
bax <- c("ba_x1","ba_x2","ba_x3","ba_x4","ba_x5","ba_x6","ba_x7","ba_x8",
        "ba_x9","ba_x10","ba_x11","ba_x12","ba_x13","ba_x14","ba_x15","ba_x16",
        "ba_x17","ba_x18","ba_x19","ba_x20","ba_x21","ba_x22","ba_x23","ba_x24",
        "ba_x25","ba_x26","ba_x27","ba_x28","ba_x29","ba_x30","ba_x31","ba_x32",
        "ba_x33","ba_x34","ba_x35","ba_x36","ba_x37","ba_x38","ba_x39","ba_x40",
        "ba_x41","ba_x42","ba_x43","ba_x44","ba_x45","ba_x46","ba_x47","ba_x48",
        "ba_x49","ba_x50","ba_x51","ba_x52","ba_x53","ba_x54","ba_x55","ba_x56",
        "ba_x57","ba_x58","ba_x59","ba_x60","ba_x61","ba_x62","ba_x63","ba_x64",
        "ba_x65","ba_x66","ba_x67","ba_x68","ba_x69","ba_x70","ba_x71","ba_x72",
        "ba_x73","ba_x74","ba_x75","ba_x76","ba_x77","ba_x78","ba_x79","ba_x80",
        "ba_x81","ba_x82","ba_x83","ba_x84","ba_x85","ba_x86","ba_x87","ba_x88",
        "ba_x89","ba_x90","ba_x91","ba_x92","ba_x93","ba_x94","ba_x95","ba_x96",
        "ba_x97","ba_x98","ba_x99","ba_x100","ba_x101","ba_x102","ba_x103",
        "ba_x104","ba_x105","ba_x106","ba_x107","ba_x108","ba_x109","ba_x110",
        "ba_x111","ba_x112","ba_x113","ba_x114","ba_x115","ba_x116","ba_x117",
        "ba_x118","ba_x119","ba_x120","ba_x121","ba_x122","ba_x123","ba_x124",
        "ba_x125","ba_x126","ba_x127","ba_x128")
bay <- c("ba_y1","ba_y2","ba_y3","ba_y4","ba_y5","ba_y6","ba_y7","ba_y8",
         "ba_y9","ba_y10","ba_y11","ba_y12","ba_y13","ba_y14","ba_y15","ba_y16",
         "ba_y17","ba_y18","ba_y19","ba_y20","ba_y21","ba_y22","ba_y23","ba_y24",
         "ba_y25","ba_y26","ba_y27","ba_y28","ba_y29","ba_y30","ba_y31","ba_y32",
         "ba_y33","ba_y34","ba_y35","ba_y36","ba_y37","ba_y38","ba_y39","ba_y40",
         "ba_y41","ba_y42","ba_y43","ba_y44","ba_y45","ba_y46","ba_y47","ba_y48",
         "ba_y49","ba_y50","ba_y51","ba_y52","ba_y53","ba_y54","ba_y55","ba_y56",
         "ba_y57","ba_y58","ba_y59","ba_y60","ba_y61","ba_y62","ba_y63","ba_y64",
         "ba_y65","ba_y66","ba_y67","ba_y68","ba_y69","ba_y70","ba_y71","ba_y72",
         "ba_y73","ba_y74","ba_y75","ba_y76","ba_y77","ba_y78","ba_y79","ba_y80",
         "ba_y81","ba_y82","ba_y83","ba_y84","ba_y85","ba_y86","ba_y87","ba_y88",
         "ba_y89","ba_y90","ba_y91","ba_y92","ba_y93","ba_y94","ba_y95","ba_y96",
         "ba_y97","ba_y98","ba_y99","ba_y100","ba_y101","ba_y102","ba_y103",
         "ba_y104","ba_y105","ba_y106","ba_y107","ba_y108","ba_y109","ba_y110",
         "ba_y111","ba_y112","ba_y113","ba_y114","ba_y115","ba_y116","ba_y117",
         "ba_y118","ba_y119","ba_y120","ba_y121","ba_y122","ba_y123","ba_y124",
         "ba_y125","ba_y126","ba_y127","ba_y128")

baz <- c("ba_z1","ba_z2","ba_z3","ba_z4","ba_z5","ba_z6","ba_z7","ba_z8",
         "ba_z9","ba_z10","ba_z11","ba_z12","ba_z13","ba_z14","ba_z15","ba_z16",
         "ba_z17","ba_z18","ba_z19","ba_z20","ba_z21","ba_z22","ba_z23","ba_z24",
         "ba_z25","ba_z26","ba_z27","ba_z28","ba_z29","ba_z30","ba_z31","ba_z32",
         "ba_z33","ba_z34","ba_z35","ba_z36","ba_z37","ba_z38","ba_z39","ba_z40",
         "ba_z41","ba_z42","ba_z43","ba_z44","ba_z45","ba_z46","ba_z47","ba_z48",
         "ba_z49","ba_z50","ba_z51","ba_z52","ba_z53","ba_z54","ba_z55","ba_z56",
         "ba_z57","ba_z58","ba_z59","ba_z60","ba_z61","ba_z62","ba_z63","ba_z64",
         "ba_z65","ba_z66","ba_z67","ba_z68","ba_z69","ba_z70","ba_z71","ba_z72",
         "ba_z73","ba_z74","ba_z75","ba_z76","ba_z77","ba_z78","ba_z79","ba_z80",
         "ba_z81","ba_z82","ba_z83","ba_z84","ba_z85","ba_z86","ba_z87","ba_z88",
         "ba_z89","ba_z90","ba_z91","ba_z92","ba_z93","ba_z94","ba_z95","ba_z96",
         "ba_z97","ba_z98","ba_z99","ba_z100","ba_z101","ba_z102","ba_z103",
         "ba_z104","ba_z105","ba_z106","ba_z107","ba_z108","ba_z109","ba_z110",
         "ba_z111","ba_z112","ba_z113","ba_z114","ba_z115","ba_z116","ba_z117",
         "ba_z118","ba_z119","ba_z120","ba_z121","ba_z122","ba_z123","ba_z124",
         "ba_z125","ba_z126","ba_z127","ba_z128")


t1_ba_x <- read.table("./UCI HAR Dataset/train/Inertial Signals/body_acc_x_train.txt",
                      col.names=bax)
t1_ba_x$ID <- seq(1,7352, by=1)
t1_ba_y <- read.table("./UCI HAR Dataset/train/Inertial Signals/body_acc_y_train.txt",
                      col.names=bay)
t1_ba_y$ID <- seq(1,7352, by=1)
t1_ba_z <- read.table("./UCI HAR Dataset/train/Inertial Signals/body_acc_z_train.txt",
                      col.names=baz)
t1_ba_z$ID <- seq(1,7352, by=1)


data  <- list(t1_ba_x,t1_ba_y,t1_ba_z)
datos <- join_all(data)

summ <- summary(datos)
