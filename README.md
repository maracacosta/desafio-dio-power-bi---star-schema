# desafio-dio-power-bi---star-schema

Desafio DIO - Modelagem Dimensional (Star Schema)

## 📋 Descrição

Modelagem dimensional **Star Schema** focada na **análise de professores** conforme especificação do desafio DIO.

**Objetivo**: Criar diagrama dimensional com tabela fato + dimensões, foco em professores (cursos, departamentos, disciplinas). 

## 🏗️ Estrutura do Star Schema
        ┌─────────────────┐
        │  DimProfessor   │ ← Nome, Titulação, Regime
        │     (5 reg)     │
        └─────────┬───────┘
                  │
┌─────────────────┴──┐  ┌─────────────────┐  ┌──────────────────┐
│   DimCurso (3)     │  │ DimDisciplina   │  │ DimDepartamento  │
│ NomeCurso, Modal.  │  │  (4 reg)        │  │   (3 reg)        │
└────────────────────┘  └─────────────────┘  └──────────────────┘
         │                       │                    │
         └─────────┬──────────────┼────────────────────┼──────────┐
                   │              │                    │          │
                   ▼              ▼                    ▼          ▼
            ┌─────────────────────────────────────────────────────┐
            │        FatoProfessorOferta (5 registros)            │
            │  Medidas: CH, Turmas, Matrículas                    │
            │  FKs: ProfessorID, CursoID, DisciplinaID, etc.      │
            └─────────────────────────────────────────────────────┘
                            │
                            │
                    ┌───────▼───────┐
                    │   DimData     │ ← Ano, Mês, Trimestre
                    │    (5 reg)    │
                    └────────────────┘


## 📊 Tabelas Criadas

| Tabela | Tipo | Registros | Finalidade |
|--------|------|-----------|------------|
| `FatoProfessorOferta` | **FATO** | 5 | Medidas de oferta |
| `DimProfessor` | DIM | 5 | Detalhes professores |
| `DimCurso` | DIM | 3 | Detalhes cursos |
| `DimDisciplina` | DIM | 4 | Detalhes disciplinas |
| `DimDepartamento` | DIM | 3 | Departamentos |
| `DimData` | DIM | 5 | Calendário (criada) |

Mara Costa - Business Analyst | Data Analytics
14/03/2026

                    


