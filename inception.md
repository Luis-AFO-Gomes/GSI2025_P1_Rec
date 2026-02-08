# Inception — Business Modeling & Requirements

## 1) Business Modeling

### 1.1 Stakeholders
| Stakeholder | Interesses / necessidades |
|---|---|
| Organização do campeonato | Definir formato do campeonato, lista de tipos de ocorrência, calendário e equipas |
| Clubes/Equipas | Gerir plantéis (jogadores) e participação em jogos/jornadas |
| Oficiais de jogo (árbitros/mesa) | Registar resultado e ocorrências (eventos) |
| Jogadores | Identificação e histórico por clubes |
| Público/Media (opcional) | Consultar calendário e resultados |

### 1.2 Glossário (mínimo)
| Termo | Definição |
|---|---|
| Campeonato | Competição com equipas e jogos; formato: eliminação, pontuação ou híbrido por fases |
| Jornada | “Ronda” do calendário; cada equipa joga 1 jogo (ou está dispensada) |
| Jogo | Evento entre 2 equipas com data, resultado e ocorrências |
| Ocorrência | Evento registado durante o jogo (tipo + jogadores + tempo de jogo) |
| Trajecto desportivo | Intervalos de tempo em que um jogador representou um clube (sem sobreposição) |

### 1.3 Regras de negócio (BR)
| ID | Regra |
|---|---|
| RB-01 | Cada jogo é entre **duas equipas ou jogadores** |
| RB-02 | Formato do campeonato: eliminação directa / pontuação / híbrido por fases |
| RB-03 | O calendário é dividido por jornadas e definido **antes** do 1º jogo |
| RB-04 | Em cada jornada, cada equipa participa em **um e só um** jogo; pode haver dispensa |
| RB-05 | Jogo tem data, resultado final e lista de ocorrências |
| RB-06 | Ocorrência: tipo (lista definida pela organização), jogador(es) intervenientes e tempo de jogo |
| RB-07 | Jogador: dados civis, ano de início, função em campo |
| RB-08 | Um jogador não pode representar duas equipas em simultâneo (histórico por intervalos) |

---

## 2) Requisitos

### 2.1 Requisitos funcionais (FR) — visão de Funcionalidade Mínima (MVP)
|  ID  | Requisito |
|---|---|
| + FR-01 | Criar campeonato e seleccionar formato (eliminação / pontuação / híbrido por fases) |
| + FR-02 | Registar equipas participantes |
| + FR-03 | Registar jogadores de cada equipa e respetiva função |
| + FR-04 | Definir calendário por jornadas antes do início do campeonato |
| + FR-05 | Criar jogos por jornada garantindo regra “1 jogo por equipa por jornada” |
| + FR-06 | Registar resultado final do jogo |
| - FR-07 | Registar ocorrências do jogo (tipo + jogadores + tempo) |
| - FR-08 | Manter histórico do jogador por clubes com intervalos sem sobreposição |
| + FR-09 | Consultar calendário por jornada e resultados (por jornada e por equipa) |

### 2.2 Casos de uso (UC) — resumo
| UC | Ator | Resultado |
|---|---|---|
| + UC-01 Gerir Campeonato | Organização | campeonato criado e configurado |
| + UC-02 Gerir Equipas | Organização | equipas registadas como participantes |
| - UC-03 Gerir Plantel | Clube/Organização | jogadores registados com função |
| + UC-04 Planear Calendário | Organização | jornadas e jogos definidos antes do arranque |
| + UC-05 Registar Resultado | Oficial/Organização | resultado final registado |
| - UC-06 Registar Ocorrências | Oficial | lista de ocorrências com tipo/jogadores/tempo |
| - UC-07 Manter Trajecto | Clube/Organização | intervalos por clube sem sobreposição |
| + UC-08 Consultar Calendário/Resultados | Público/Clubes | pesquisa por jornada/equipa |

**Notas**
- \+ : Requisitos/Caso de Uso de implementação **obrigatória**
- \- : Requisitos/Caso de Uso de implementação **facultativa**
- Para facilitar a definição, pode-se considerar que, em desportos individuais, cada jogador é uma equipa de 1
  - Pode-se crear mecanismos para implementar este definição aquando da criação de equipa/jogador
  