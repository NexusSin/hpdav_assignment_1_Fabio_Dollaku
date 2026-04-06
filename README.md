# HPDAV Individual Assignment — Interactive Data Visualizations

Visualization app for the US Communities and Crime dataset. Built on top of the [Tuto5-MultiDim-Redux](https://github.com/nicolasmedoc/Tuto5-MultiDim-Redux.git) template from Nicolas Médoc, extended with linked views and brushing.

There are two views: a scatterplot where you pick any two attributes for the axes, and a hierarchy (treemap, circle packing, or tree) that groups communities by state. Select something in one view and the other one reacts.

## Running the app

Node.js v16+ required.

```bash
npm install
npm start
```

Goes to `http://localhost:5173` by default (Vite).

For production:

```bash
npm run build
npm run serve
```

## How it works

- Use the dropdowns to pick which attributes go on x and y in the scatterplot
- Drag a selection rectangle on the scatterplot — the hierarchy highlights those communities
- Click a node in the hierarchy — the scatterplot highlights the matching points
- Switch layout (treemap / circle packing / tree) from the dropdown on the right
- The hierarchy value attribute is separate from the scatterplot axes, so you can change it independently

## Dataset

US Communities and Crime (UCI ML Repository). 1,355 communities, 46 states, 100+ normalized attributes on income, housing, policing, and crime. The original CSV has missing values marked as "?" — those get filtered out before rendering.

## Stack

- React 18
- D3.js 7
- Redux Toolkit
- PapaParse
- Vite

## Structure

```
src/
|
|-- components/
|   |-- scatterplot/       # Scatterplot-d3.js + ScatterplotContainer.jsx
|   |-- hierarchy/         # Hierarchy-d3.js + HierarchyContainer.jsx
|
|-- redux/
|   |-- DataSetSlice.js          # loads CSV into store
|   |-- ItemInteractionSlice.js  # selectedItems[], brushedItems[], hoveredItem{}
|
|-- utils/
|   |-- hierarchyBuilder.js      # groups communities by state via FIPS codes
|
|-- templates/             # d3+react separation of concerns template
|
|-- App.jsx
|-- store.js
```

## Author

Fabio Dollaku — University of Luxembourg, HPDAV, March 2026
