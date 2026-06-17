# Football Match Momentum Analysis

Interactive football match momentum analysis using open event data.

This project recreates a football match momentum visualization for the 2022 FIFA World Cup Final between Argentina and France, using StatsBomb Open Data and a custom weighted attacking threat model.

## Objective

The goal of this project is to estimate and visualize which team generated more attacking threat during different phases of the match.

Instead of counting simple possession or total passes, the model assigns value to football actions that are more directly related to attacking danger.

## Match Analyzed

**Argentina 3 - 3 France**  
FIFA World Cup Final 2022  
Match ID: `3869685`

## Data Source

The project uses StatsBomb Open Data, accessed through the `statsbombpy` Python package.

## Methodology

A custom momentum score is calculated from selected event types:

- Shots
- Progressive passes
- Progressive carries
- Successful dribbles
- High recoveries
- Interceptions
- High pressures

The model applies higher weights to events that generate attacking threat, such as shots with high xG, progressive actions into advanced zones and goals.

The final momentum curve is calculated by aggregating scores by minute and smoothing the difference between both teams.

## Tools

- Python
- pandas
- numpy
- Plotly
- StatsBombPy

## Output

The project produces an interactive momentum chart showing:

- Argentina momentum
- France momentum
- Net momentum curve
- Goal timeline
- Match phases

## Project Structure

```text
football-momentum-analysis/
├── README.md
├── requirements.txt
├── notebooks/
│   └── momentum_analysis.ipynb
├── outputs/
│   └── interactive_momentum_chart.html
└── data/
    └── README.md