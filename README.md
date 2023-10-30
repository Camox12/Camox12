# Código para generar el gráfico
library(ggplot2)
# Definir las curvas de oferta y demanda agregadas
OA <- function(P) {100 + 0.5*P}
DA <- function(P) {200 - 0.25*P}
OALP <- function(P) {150}
# Definir los niveles de precios y producto de equilibrio
Pe <- 133.33
Ye <- 166.67
# Crear un data frame con los datos para el gráfico
df <- data.frame(
  P = seq(0, 200, by = 10),
  OA = OA(seq(0, 200, by = 10)),
  DA = DA(seq(0, 200, by = 10)),
  OALP = OALP(seq(0, 200, by = 10))
)
# Generar el gráfico con ggplot2
ggplot(df, aes(x = P)) +
  geom_line(aes(y = OA), color = "blue", size = 1.2) +
  geom_line(aes(y = DA), color = "red", size = 1.2) +
  geom_line(aes(y = OALP), color = "green", size = 1.2) +
  geom_vline(xintercept = Pe, linetype = "dashed") +
  geom_hline(yintercept = Ye, linetype = "dashed") +
  annotate("text", x = Pe + 10, y = Ye + 10, label = "E", size = 6) +
  scale_x_continuous(name = "Nivel de precios (P)", limits = c(0, 200)) +
  scale_y_continuous(name = "Producto (Y)", limits = c(0, 200)) +
  theme_bw() +
  ggtitle("Equilibrio de largo plazo en Italia")
