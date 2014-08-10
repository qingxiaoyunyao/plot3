plot3
=====

## read data into R
data <- read.csv2("household_power_consumption.txt", header = TRUE, as.is = TRUE) 

## add a new variable "time" which denotes the time and date
time <- strptime(paste(data$Date, data$Time), "%d/%m/%Y %H:%M:%S")

data$time <- time

## transform "Date" variable to Date type
data$Date <- as.Date(data$Date, "%d/%m/%Y")

## get the data from 01/02/2007 to 02/02/2007
a <- data[data$Date >= as.Date("01/02/2007", "%d/%m/%Y") & data$Date <= as.Date("02/02/2007","%d/%m/%Y"),]

## draw the picture
with(a, plot(time, Sub_metering_1, type = "l", col = "black", ylab = "Energy sub metering", xlab = ""))

with(a, lines(time, Sub_metering_2, col = "red"))

with(a, lines(time, Sub_metering_3, col = "blue"))

legend("topright", lty = 1, col = c("black", "red", "blue"), legend = c("Sub_metering_1", "Sub_metering_2", "Sub_metering_3"))

## save the picture in plot3.png
dev.copy(png, width = 480, height = 480, file = "plot3.png")

dev.off()

Exploratory Data Analysis/ assignment 1/ plot3
