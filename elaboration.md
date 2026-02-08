# Elementos a implementar

## 3) Modelo conceptual

### 3.1 Entidades (sugestão)
As entidades e componentes a implementar na realidade podem ser diferentes das propostas
Ter em atenção os requisitos obrigatórios/facultativos para definir as entidades de componentes que são implementados

| Entidade | Atributos chave | Observações |
|---|---|---|
| Campeonato | id, nome, época, formato | formato: eliminação/pontuação/híbrido |
| Fase | id, campeonato_id, nome, formato | só para formato híbrido (por fases) |
| Equipa/Clube | id, nome | participante |
| Participação | campeonato_id, equipa_id | equipas presentes no campeonato |
| Jornada | id, campeonato_id (ou fase_id), número | componente do calendário |
| Jogo | id, jornada_id, data, equipaA_id, equipaB_id, resultado_final | sempre 2 equipas |
| TipoOcorrencia | id, nome | lista definida pela organização |
| Ocorrencia | id, jogo_id, tipo_id, tempo_jogo | liga a jogadores intervenientes |
| OcorrenciaJogador | ocorrencia_id, jogador_id | 1..N jogadores por ocorrência |
| Jogador | id, nome, doc_id, ano_inicio, funcao | dados civis + função + ano início |
| TrajectoJogadorClube | id, jogador_id, clube_id, dt_inicio, dt_fim | intervalos sem sobreposição |
| DispensaJornada | jornada_id, equipa_id | equipa dispensada (não joga nessa jornada) |

### 3.2 Restrições/validações críticas (implementáveis na BD)
| ID | Validação | Como garantir |
|---|---|---|
| V-01 | Em cada jornada, uma equipa não pode estar em 2 jogos | constraint/unique + verificação na criação do jogo |
| V-02 | Dispensa só pode existir se a equipa não tiver jogo nessa jornada | constraint + lógica de aplicação |
| V-03 | Trajecto do jogador sem sobreposição de datas | constraint (exclusion/trigger) + validação na app |
| V-04 | Ocorrência tem tipo válido e tempo de jogo válido | FK + checks (intervalo configurável) |

---

## 4) Arquitectura da aplicação

### 4.1 Componentes (módulos/classe)
- **Gestão de Campeonatos**: campeonato, fases (se híbrido), participantes
- **Calendário**: jornadas, jogos, dispensa
- **Jogo**: resultados e ocorrências
- **Atletas/Histórico**: jogadores, trajecto por clube
- **Consulta**: calendário e resultados

### 4.2 Funcionalidades da aplicação (MVP)
| objecto | Descrição |
|---|---|
| 'Campeonato' | criar/listar campeonatos |
| 'Campeonato' | gerir fases (se híbrido) |
| 'Campeonato' | gerir participantes |
| 'Campeonato' | criar/listar jornadas |
| 'Jornada' | criar jogo na jornada |
| 'Jornada' | marcar equipa dispensada |
| 'Jogo' | registar resultado final |
| 'Jogo' | criar/listar ocorrências |
| 'Ocorrências' | gerir lista de tipos |
| 'Jogadores' | criar/listar jogadores |
| 'Jogadores' | gerir trajecto |

### 4.3 Menus (MVP)
- Gestão do campeonato (formato + participantes)
- Calendário (jornadas + criação de jogos + dispensas)
- Ficha do jogo (resultado + ocorrências)
- Gestão de jogadores (perfil + trajecto)
- Consulta (calendário e resultados por jornada/equipa)


