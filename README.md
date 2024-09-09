# Analyse Financière des Rentabilités Mensuelles d'Air Liquide (2014-2023)<br>
## Contexte du Projet
Dans le cadre d’un projet universitaire visant à analyser les caractéristiques financières d’une action cotée en bourse parisienne depuis 2013, nous avons choisi d’étudier l’action Air Liquide. La période d’analyse s’étend du 1er janvier 2014 au 1er décembre 2023, soit une durée de 10 ans. Les données ont été collectées sur le site Yahoo Finance, en utilisant les prix de clôture des actions.
## Méthodologie
Les rentabilités mensuelles simples ont été calculées à partir des prix de clôture ajustés, suivies du calcul des statistiques descriptives : moyenne, écart-type, minimum, maximum, skewness et kurtosis. Ces mesures statistiques permettent d’appréhender la performance globale du titre ainsi que sa volatilité.
## Statistiques descriptives
-Rentabilité mensuelle moyenne : 1,005 %. Ce chiffre indique une performance positive et stable sur l’ensemble de la période.  <br>
-Médiane : 1,32 %. La médiane, supérieure à la moyenne, indique que plus de la moitié des rendements mensuels étaient supérieurs à la moyenne, ce qui suggère la présence de quelques mois de rendements négatifs ou plus faibles qui ont tiré la moyenne vers le bas. 

#### Statistiques des Quartiles :
. 1er quartile (1st Qu.) : -2,379 %. Un quart des rendements étaient inférieurs à cette valeur, indiquant des périodes de sous-performance. <br>
. 3e quartile (3rd Qu.) : 4,254 %. Un quart des rendements étaient supérieurs à ce niveau, montrant des périodes de surperformance notable. <br>
. Rentabilité minimale : -13,454 %. Cela correspond à une chute significative de l’action sur un mois, probablement en raison d’un événement économique majeur. <br>
. Rentabilité maximale : 12,538 %. Cela reflète une forte hausse de l’action sur un mois, peut-être liée à des facteurs spécifiques à l’entreprise. <br>

#### Skewness et Kurtosis
. Skewness (Asymétrie) : -0,0925. Cette skewness légèrement négative indique une légère asymétrie de la distribution des rendements vers la gauche, signifiant une tendance à avoir des rendements mensuels négatifs extrêmes. Toutefois, la faible valeur de skewness suggère que ces rendements extrêmes ne sont pas fréquents. <br>

. Kurtosis (Aplatissement) : -0,0294. Une kurtosis légèrement négative indique une distribution légèrement plus plate que la normale (platykurtique), avec des queues fines. Cela signifie que les rendements extrêmes, bien que présents, ne sont pas aussi fréquents qu’attendu dans une distribution normale. Cela rassure quant à la stabilité des rendements, mais n'exclut pas le risque d’événements extrêmes.

## Interprétation des Graphiques
#### Graphique des Séries Temporelles:<br>
![graphique_des_series_temporelles](https://github.com/user-attachments/assets/e627301a-a9f6-4f33-99e0-87e189cca9af) <br>
Ce graphique montre la volatilité des rentabilités mensuelles d'Air Liquide de 2014 à 2023.<br> 

Volatilité : Les rendements mensuels présentent une volatilité notable, oscillant entre +10 % et -10 %.
Périodes de forte rentabilité : Des pics de rentabilité, souvent supérieurs à 5 %, apparaissent notamment en 2017, 2019 et 2021.
Périodes de pertes : Des baisses importantes (jusqu’à -10 %) sont visibles, particulièrement en 2018, 2020 et 2022, potentiellement liées à des événements macroéconomiques (comme la crise de la COVID-19).


#### Histogramme des Rentabilités Mensuelles:<br>
![histogramme](https://github.com/user-attachments/assets/5e61ce18-f8f9-4cc8-bfb5-eb78770b758c) <br>
Cet histogramme montre la distribution des rentabilités mensuelles sur la période étudiée.<br>

Distribution : La majorité des rendements sont positifs, concentrés entre 0 % et 5 %.
Extrêmes : Quelques rendements extrêmes sont observés (jusqu'à -15 % et +15 %), mais ils sont rares.
Skewness et Kurtosis : L'histogramme confirme la skewness légèrement négative et la kurtosis faible. Les pertes semblent être un peu plus extrêmes que les gains.    

![densité](https://github.com/user-attachments/assets/75830856-d3dd-409f-b1fe-b121f0aaeb30) <br>



### Q-Q Plot<br>
![Quantile](https://github.com/user-attachments/assets/2d407bc6-dbc4-4339-b62a-402355adf487) <br>
Le Normal Q-Q Plot compare les rendements mensuels d’Air Liquide à une distribution normale. <br>

Alignement : La plupart des points sont alignés avec la droite de référence, suggérant une distribution des rendements proche de la normale.
Déviations aux extrémités : Quelques déviations mineures aux extrémités suggèrent que les rendements extrêmes sont légèrement plus prononcés que dans une distribution normale, ce qui corrobore les résultats de la skewness et de la kurtosis.<br>

### Nuage de points des deux séries de rentabilités avec celles de l’indice CAC 40 

![nuage_de_point](https://github.com/user-attachments/assets/ea004d46-c1f4-43ea-a6cd-9dcc673da731) <br>
#### Risque spécifique et risque systématique

• Le risque associé à un actif financier peut se décomposer en un risque systématique et un risque spécifique.<br>
• Le risque spécifique, propre au titre, est aussi appelé risque diversifiable (ou intrinsèque). <br>
• le risque systématique, risque dû aux variations du marché, est dit risque non diversifiable (ou risque de marché). <br>
Risque d’une action = risque systématique + risque spécifique <br>

$$
R_{\text{TCKR}, t} = \alpha + \beta R_{\text{CAC}, t} + \epsilon_t
$$

• La mesure du risque systématique se fait par le calcul d’un coefficient de corrélation, appelé bêta, qui est défini comme la volatilité du titre. <br>
• L’estimation du bêta peut se faire à l’aide du modèle du marché, sur la base de données passées. <br>
• Il exprime la sensibilité de la valeur du titre aux variations du marché :<br>

 $\beta_{\ TCKR} = \frac{\text{Cov}(R_{\text{TCKR}}, R_{\text{CAC}})}{\text{Var}(R_{\text{CAC}})}$ <br>

Rappelons la formule de covariance :<br>

$$
\text{Cov}(R_{\text{TCKR}}, R_{\text{CAC}}) = \frac{1}{n-1} \sum_{t=1}^{n} \left( (R_{\text{TCKR}, t} - \overline{R_{\text{TCKR}}}) (R_{\text{CAC}, t} - \overline{R_{\text{CAC}}}) \right)
$$


```r

# 1) On a sélectionné l'action Air Liquide de 01/01/2014 jusqu'à 01/12/2023
library(quantmod)

# On fixe les dates qui définissent la période
debut = "2014-01-01"
fin = "2023-12-01"

# On obtient les données de l'action Air Liquide sur le site Yahoo Finance
TCKR <- "AI.PA"
getSymbols(TCKR, src = "yahoo", from = debut, to = fin, periodicity = "monthly")

# On regarde les valeurs associées à l'objet
names(AI.PA)

# Charger les données téléchargées dans un objet de type xts
AL_xts <- as.xts(get(TCKR))

# Renommer les colonnes : "Open", "High", "Low", "Close", "Volume", "Adjusted"
colnames(AL_xts) <- c("Open", "High", "Low", "Close", "Volume", "Adjusted")

# 2) Calcul des rentabilités mensuelles simples à partir des prix à la clôture
monthly_returns_AL <- monthlyReturn(AL_xts$Close, type = "arithmetic")
class(monthly_returns_AL)
head(monthly_returns_AL)

# Ajoutons NA comme 1er valeur dans le vecteur
monthly_returns_AL[1] <- NA
head(monthly_returns_AL, 10)

# 3) Calcul des statistiques descriptives suivantes des rentabilités: La moyenne, l'écart-type, le minimum, le maximum,
# le skewness et le kurtosis
summary(monthly_returns_AL) # Pour calculer le Max, le Min, la Moyenne

# Calculer chacune des statistiques descriptives
library("e1071")
mean_return <- mean(monthly_returns_AL, na.rm = TRUE)
cat("La MOYENNE:", mean_return, "\n") # Afficher la moyenne

std_return <- sd(monthly_returns_AL, na.rm = TRUE)
cat("Ecart-type:", std_return, "\n") # Afficher l'Ecart-type

min_return <- min(monthly_returns_AL, na.rm = TRUE)
cat("Minimum:", min_return, "\n")

max_return <- max(monthly_returns_AL, na.rm = TRUE)
cat("Maximum:", max_return, "\n")

# skewness est une mesure statistique qui décrit l'asymétrie de la distribution d'un ensemble de données par rapport à la moyenne.
skewness_return <- skewness(monthly_returns_AL, na.rm = TRUE, type = 3)
cat("Skewness:", skewness_return, "\n") # Afficher Skewness

kurtosis_value <- kurtosis(monthly_returns_AL, na.rm = TRUE, type = 3)
cat("Kurtosis", kurtosis_value, "\n")

# 4) Traçons les graphiques pour les rentabilités de AI.PA:

# Graphique des séries temporelles
plot(monthly_returns_AL, main = "Graphique des séries temporelles des rentabilités Air Liquide", xlab = "Date", ylab = "Rentabilité mensuelle")

# Histogramme
hist(monthly_returns_AL, main = "Histogramme des rentabilités Air Liquide", xlab = "Rentabilité mensuelle", ylab = "Densité")

# Densité empirique (kernel density)
densité <- density(monthly_returns_AL, na.rm = TRUE)
plot(densité, main = "Densité empirique des rentabilités Air Liquide", xlab = "Rentabilité mensuelle", ylab = "Densité")
polygon(densité, col = "lightblue", border = "red") # polygon remplit la zone sous la courbe de densité avec la couleur "lightblue" et un bord "rouge"

# Graphique Quantile-Quantile (Normal probability plot)
qqnorm(monthly_returns_AL)
qqline(monthly_returns_AL, col = 2)

# 5) Téléchargons les données sur l'Indice CAC40 (sur la même période et la même fréquence (mensuelle))
# On obtient les données du CAC40
getSymbols("^FCHI", src = "yahoo", from = debut, to = fin, periodicity = "monthly")

cac_40_xts <- as.xts(get("FCHI"))
# Renommer les colonnes CAC40
colnames(cac_40_xts) <- c("Open", "High", "Low", "Close", "Volume", "Adjusted")

# Calculons des rentabilités mensuelles simples de l'indice CAC40 à partir des prix à la clôture
monthly_returns_cac40 <- monthlyReturn(cac_40_xts$Close, type = "arithmetic")
# Ajoutons NA comme 1er valeur dans le vecteur
monthly_returns_cac40[1] <- NA

head(monthly_returns_cac40, 10) # 10 premières rentabilités mensuelles
tail(monthly_returns_cac40, 10) # 10 dernières rentabilités mensuelles

# Créer un tableau de la rentabilité d'Air Liquide et l'Indice CAC40
return_cac40_AL <- cbind(monthly_returns_AL, monthly_returns_cac40)
colnames(return_cac40_AL) <- c("return_AL", "return_cac40")

# 6) Traçons le nuage de points des 2 séries de rentabilités

# utilisons la librairie ggplot2
library(ggplot2)
courbe_nuage <- ggplot(return_cac40_AL, aes(x = monthly_returns_cac40, y = monthly_returns_AL)) + geom_point()
courbe_nuage <- courbe_nuage + xlab("Rentabilité mensuelle de l'indice CAC 40") + ylab("Rentabilité mensuelle d'Air Liquide") + ggtitle("Nuage de points des rentabilités")
courbe_nuage <- courbe_nuage + geom_smooth(method = "lm", color = "firebrick1", se = FALSE) # Ajoutons la droite de tendance linéaire

# 7) Calculons la bêta de marché du titre Air Liquide suivant la régression

# Effectuer la régression linéaire
regression <- lm(monthly_returns_AL ~ monthly_returns_cac40)
coefficients <- coef(regression)

# Le coefficient de pente estimé est le bêta de marché
beta <- coefficients["monthly_returns_cac40"]

# Afficher le bêta de marché
cat("beta:", beta)
