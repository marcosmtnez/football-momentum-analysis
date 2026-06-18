# Football Match Momentum Analysis

Interactive football match momentum analysis using StatsBomb Open Data.

This project builds a custom momentum model for the **Argentina vs France 2022 FIFA World Cup Final**, estimating which team generated more attacking threat throughout the match.

## Interactive Visualization

The interactive version of the chart is available here:

[Open Interactive Momentum Chart](https://marcosmtnez.github.io/football-momentum-analysis/interactive_momentum_chart.html)

## Project Preview

![Momentum Chart Preview](outputs/momentum_chart_preview.png)

## Project Overview

Momentum charts are increasingly used in football broadcasts to show how the rhythm and control of a match changes over time.

The objective of this project was to explore what could be behind this type of visualization and build a custom version using event-level football data.

Instead of relying only on traditional statistics such as possession, total passes or total shots, this project estimates attacking momentum by assigning value to actions that move a team closer to creating danger.

The final model produces an interactive visualization that shows how attacking threat evolved during one of the most dramatic football matches ever played.

## Match Analyzed

**Argentina vs France**
**2022 FIFA World Cup Final**
Final score: Argentina 3–3 France
Argentina won after penalties.

This match was selected because it offers a very strong momentum narrative:

* Argentina dominated large periods of the match.
* France produced a dramatic comeback through Kylian Mbappé.
* Extra time created several shifts in control.
* The penalty shootout was excluded from the momentum model to focus only on open-play and match-time events.

## Data Source

The project uses **StatsBomb Open Data**, accessed through the `statsbombpy` Python package.

Event data includes detailed match actions such as:

* Shots
* Passes
* Carries
* Dribbles
* Pressures
* Interceptions
* Recoveries

## Methodology

A custom weighted attacking threat index was created using event-level data.

The model considers several types of actions:

* Shots and expected goals (xG)
* Progressive passes
* Progressive carries
* Successful dribbles
* High recoveries
* Interceptions
* Pressures in advanced areas

Each event is assigned a value depending on its attacking relevance. The values are then aggregated by minute, comparing Argentina and France to estimate net momentum throughout the match.

Positive values represent Argentina momentum, while negative values represent France momentum.

The final signal is smoothed using a rolling window to make the match rhythm easier to interpret visually.

## Key Design Decisions

Several decisions were made to make the model more realistic:

* Penalty shootout events were removed from the analysis.
* Goalkeeper long clearances were filtered out to avoid artificial progressive actions.
* Progressive actions were only considered when they moved the ball meaningfully towards goal.
* Shots were weighted using expected goals.
* Goals were highlighted as key events but not allowed to fully dominate the momentum curve.
* Match phases such as half-time, full-time and extra time were added to improve interpretation.

## Technologies Used

* Python
* pandas
* numpy
* Plotly
* StatsBomb Open Data
* statsbombpy
* Jupyter Notebook
* GitHub Pages

## Repository Structure

```text
football-momentum-analysis/
├── data/
│   └── README.md
├── notebooks/
│   └── momentum_analysis.ipynb
├── outputs/
│   ├── interactive_momentum_chart.html
│   └── momentum_chart_preview.png
├── interactive_momentum_chart.html
├── README.md
├── requirements.txt
└── .gitignore
```

## How to Run the Project

Clone the repository:

```bash
git clone https://github.com/marcosmtnez/football-momentum-analysis.git
cd football-momentum-analysis
```

Install the required packages:

```bash
pip install -r requirements.txt
```

Run the notebook:

```bash
jupyter notebook notebooks/momentum_analysis.ipynb
```

The notebook generates:

* An interactive HTML chart in the project root.
* A copy of the interactive chart inside the `outputs/` folder.
* A static PNG preview for the README.

## Outputs

The main outputs of the project are:

* `interactive_momentum_chart.html`: interactive Plotly visualization published with GitHub Pages.
* `outputs/interactive_momentum_chart.html`: exported project output.
* `outputs/momentum_chart_preview.png`: static preview used in the README.

## Main Takeaway

This project shows how football event data can be transformed into a visual narrative of a match.

The final chart reflects many of the key moments from the 2022 World Cup Final: Argentina's early dominance, France's sudden comeback, the intensity of extra time and the changing rhythm of one of the most memorable finals in football history.

## Author

**Marcos Martínez**
Data Science student interested in sports analytics, football analytics and data visualization.

GitHub: [marcosmtnez](https://github.com/marcosmtnez)
