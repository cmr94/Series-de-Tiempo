# Series-de-Tiempo

install.packages("foreign")
require(foreign)
sociodemo <- read.dbf("C:\\Users\\SALA-C20\\Downloads\\SDEMT215.dbf")
sdem215<- data.frame(sociodemo)
str(sdem215)
attach(sdem215)
table(SEX)
table(EDA)
EDA1<- as.numeric(as.character(EDA))
table(EDA1)
install.packages("car")
require(car)
install.packages("memisc")
require(memisc)
install.packages("lattice")
require(lattice)
install.packages("MASS")
require(MASS)
gedad<- recode(EDA1, '1:4 =2; 5:95=1' )
###########################################


#########Ponderar casos

install.packages("questionr")
require(questionr)
c1<- wtd.table(sdem215$SEX, weights=sdem215$FAC)
table(c1)

write.csv(c1,file='C://Users//SALA-C20//Desktop//c1')
c1

tabrama<-wtd.table(sdem215$SEX, weights=sdem215$FAC)
c1.1<-round((tabrama/margin.table(tabrama))*100,2)
write.csv(c1.1,file='C://Users//SALA-C20//Desktop//c2')
c1.1

SEX1<- as.numeric(as.character(sdem215$SEX))
sdem215$SEX<- ordered(sdem215$SEX,levels=c(1,2),labels=c("Hombre", "Mujer"))
c2<- wtd.table(sdem215$SEX, weights = sdem215$FAC)
write.csv(c2,file='C://Users//SALA-C20//Desktop//c3')
View(sdem215)



sdem215$NAC_MES<- ordered(sdem215$NAC_MES,levels=c("01","02","03","04","05","06","07","08","09","10","11","12","99"),labels=c("Enero", "Febrero","Marzo","Abril","Mayo","Junio","Julio","Agosto","Septiembre","Octubre","Noviembre","Diciembre","Noespecificado"))
c3<- wtd.table(sdem215$NAC_MES, weights = sdem215$FAC)
write.csv(c3,file='C://Users//SALA-C20//Desktop//c4')
View(sdem215)
table(sdem215$NAC_MES)
