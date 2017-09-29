library(sp)
library(rgdal)

setwd(tempdir())
download.file('https://raw.github.com/oscarperpinan/solar/gh-pages/data/SIAR.csv', 'siar.csv', method='wget')
siar <- read.csv('siar.csv')
summary(siar)
siarSP <- SpatialPointsDataFrame(siar[,c(6, 7)], siar[,-c(6,7)])
writeOGR(siarSP, 'siar.geojson', 'siarSP', driver='GeoJSON')
