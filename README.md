![nuage_de_point](https://github.com/user-attachments/assets/ea004d46-c1f4-43ea-a6cd-9dcc673da731)
![Quantile](https://github.com/user-attachments/assets/2d407bc6-dbc4-4339-b62a-402355adf487)
![densité](https://github.com/user-attachments/assets/75830856-d3dd-409f-b1fe-b121f0aaeb30)
![histogramme](https://github.com/user-attachments/assets/5e61ce18-f8f9-4cc8-bfb5-eb78770b758c)
![graphique_des_series_temporelles](https://github.com/user-attachments/assets/e627301a-a9f6-4f33-99e0-87e189cca9af)

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
