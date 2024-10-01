DICIONARIO_DE_DADOS
This analysis will make an analysis of the 2009 NBA draft and will re-draft the players according with his carrer inside the NBA

1ST PROCESS:
IN: base_draft_09


RK = Rank - int
PK = Overall pick - int
TM = Draft team - str
PLAYER = player name - str #id
COLLEGE/LAST_TEAM = Formation team - str
YRS = Years in the league - int
G = Games played - int
MP = Minutes played - float
PTS = Total points - int
TRB = Total rebounds - int
AST = Total assists -int
FG_PERCENTAGE = Field goal percentage - float [0.00 - 100.00]
TP_PERCENTAGE = Three points percentage - float [0.00 - 100.00]
FT_PERCENTAGE = Free throw percentage - float [0.00 - 100.00]
MP_PER_GAME = Minutes played per game  - float
PTS_PER_GAME = Points per game - float
TRB_PER_GAME = Rebouns per game - float
AST_PER_GAME = Assits per game - float
WS = Win shares (wins contributed by a player) - float [positives and negatives]
WS_FE = Wins shares per 48 minutes - int [positives and negatives]
BPM = Box plus minus - float [positives and negatives]
VORP = Value over replacement player (value of a player when compared to his bench) - float [positives and negatives]
# Adicional columns
MVP = MVP's win - int
ASG = All star game - int 
TITLES = How many titles - int
FMVP = Finals mvp - int

OUT: base_clean
//__________________________________________________________________________________________________________________//
2ND PROCESS
IN: base_clean
In this process I will resume the base.

PLAYER = player name - str #id
YRS = Years in the league - int
G = Games played - int
MP = Minutes played - float
PTS = Total points - int
TRB = Total rebounds - int
AST = Total assists -int
FG_PERCENTAGE = Field goal percentage - float [0.0000 - 1.0000]
TP_PERCENTAGE = Three points percentage - float [0.0000 - 1.0000]
FT_PERCENTAGE = Free throw percentage - float [0.0000 - 1.0000]
MP_PER_GAME = Minutes played per game  - float
PTS_PER_GAME = Points per game - float
TRB_PER_GAME = Rebouns per game - float
AST_PER_GAME = Assits per game - float
WS = Win shares (wins contributed by a player) - float [positives and negatives]
WS_FE = Wins shares per 48 minutes - int [positives and negatives]
BPM = Box plus minus - float [positives and negatives]
VORP = Value over replacement player (value of a player when compared to his bench) - float [positives and negatives]
MVP = MVP's win - int
ASG = All star game - int 
TITLES = How many titles - int
FMVP = Finals mvp - int

OUT: base_resumed

______________________________________________________
EVERY STATISTIC HAS A MULTIPLIER      
# primeiramente, as estatisticas com maior peso, serão as de prêmios individuais (tendo pesos muito próximos ou iguais)
# segundamente, serão as métricas especias, que analisam o impacto de cada jogador dentro das quatro linhas(BPM, VORP ou WS)
# terceiramente, os dados percentuais(PER_GAME e PERCENTAGE), juntamente com a quantidade de jogos, pois demonstra o quanto aquele jogador se mantem saudavel
# em quarto lugar, a quantidade de pontos, assistências, rebotes e anos jogados (podendo seguir uma ordem decrescente ou não)


###### essas estatisticas devem ser revistas ######
YRS = * 0.550
G = * 0.650

MP = * 0.435
PTS = * 0.450
TRB = * 0.425
AST = * 0.425

# Porcentagem de acerto
FG_PERCENTAGE = * 0.450
TP_PERCENTAGE = * 0.410
FT_PERCENTAGE = * 0.425

# Volume de jogo
MP_PER_GAME = * 0.550
PTS_PER_GAME = * 0.550
TRB_PER_GAME = * 0.525
AST_PER_GAME = * 0.525

WS = * 0.650
WS_FE = * 0.700
BPM = * 0.675
VORP = * 0.675

MVP = * 1
ROY = * 0.710
DPOY = * 0.800
SMOY = * 0.775
MIP = * 0.775
ASG = * 0.750
TITLES = * 0.725
FMVP = * 0.800

# Para que essas métricas contribuam de forma proporcional elas devem ter o mesmo intervalo