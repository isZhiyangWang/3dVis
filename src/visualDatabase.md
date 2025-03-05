---
title: Explore Visualizations in 2D
toc: false
---


<style>
/* Loading overlay styling */
#loading-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(255,255,255); /* Light overlay */
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  z-index: 9999; /* Top-most */
}

/* Simple loader spinner */
.loader {
  border: 8px solid #f3f3f3; /* Light grey */
  border-top: 8px solid #007bff; /* Blue */
  border-radius: 50%;
  width: 60px;
  height: 60px;
  animation: spin 1.0s linear infinite;
  margin-bottom: 15px;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

/*! PhotoSwipe main CSS by Dmytro Semenov | photoswipe.com */

.pswp {
  --pswp-bg: #000;
  --pswp-placeholder-bg: #222;
  

  --pswp-root-z-index: 100000;
  
  --pswp-preloader-color: rgba(79, 79, 79, 0.4);
  --pswp-preloader-color-secondary: rgba(255, 255, 255, 0.9);
  
  /* defined via js:
  --pswp-transition-duration: 333ms; */
  
  --pswp-icon-color: #fff;
  --pswp-icon-color-secondary: #4f4f4f;
  --pswp-icon-stroke-color: #4f4f4f;
  --pswp-icon-stroke-width: 2px;

  --pswp-error-text-color: var(--pswp-icon-color);
}


/*
	Styles for basic PhotoSwipe (pswp) functionality (sliding area, open/close transitions)
*/

.pswp {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	z-index: var(--pswp-root-z-index);
	display: none;
	touch-action: none;
	outline: 0;
	opacity: 0.003;
	contain: layout style size;
	-webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
.description-content {
  width: 90%; 
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* Each text line with ellipsis if too long */
.desc-chart, .desc-topic, .desc-title {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  width: 100%;
}

.desc-chart, .desc-topic {
  font-size: 12px;
  color: #444;
}
.desc-title {
  font-weight: bold;
  font-size: 13px;
  color: #333;
}
/* Prevents focus outline on the root element,
  (it may be focused initially) */
.pswp:focus {
  outline: 0;
}

.pswp * {
  box-sizing: border-box;
}

.pswp img {
  max-width: none;
}

.pswp--open {
	display: block;
}

.pswp,
.pswp__bg {
	transform: translateZ(0);
	will-change: opacity;
}

.pswp__bg {
  opacity: 0.005;
	background: var(--pswp-bg);
}

.pswp,
.pswp__scroll-wrap {
	overflow: hidden;
}

.pswp__scroll-wrap,
.pswp__bg,
.pswp__container,
.pswp__item,
.pswp__content,
.pswp__img,
.pswp__zoom-wrap {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
}

.pswp__img,
.pswp__zoom-wrap {
	width: auto;
	height: auto;
}

.pswp--click-to-zoom.pswp--zoom-allowed .pswp__img {
	cursor: -webkit-zoom-in;
	cursor: -moz-zoom-in;
	cursor: zoom-in;
}

.pswp--click-to-zoom.pswp--zoomed-in .pswp__img {
	cursor: move;
	cursor: -webkit-grab;
	cursor: -moz-grab;
	cursor: grab;
}

.pswp--click-to-zoom.pswp--zoomed-in .pswp__img:active {
  cursor: -webkit-grabbing;
  cursor: -moz-grabbing;
  cursor: grabbing;
}

/* :active to override grabbing cursor */
.pswp--no-mouse-drag.pswp--zoomed-in .pswp__img,
.pswp--no-mouse-drag.pswp--zoomed-in .pswp__img:active,
.pswp__img {
	cursor: -webkit-zoom-out;
	cursor: -moz-zoom-out;
	cursor: zoom-out;
}


/* Prevent selection and tap highlights */
.pswp__container,
.pswp__img,
.pswp__button,
.pswp__counter {
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;
}

.pswp__item {
	/* z-index for fade transition */
	z-index: 1;
	overflow: hidden;
}

.pswp__hidden {
	display: none !important;
}

/* Allow to click through pswp__content element, but not its children */
.pswp__content {
  pointer-events: none;
}
.pswp__content > * {
  pointer-events: auto;
}


/*

  PhotoSwipe UI

*/

/*
	Error message appears when image is not loaded
	(JS option errorMsg controls markup)
*/
.pswp__error-msg-container {
  display: grid;
}
.pswp__error-msg {
	margin: auto;
	font-size: 1em;
	line-height: 1;
	color: var(--pswp-error-text-color);
}

/*
class pswp__hide-on-close is applied to elements that
should hide (for example fade out) when PhotoSwipe is closed
and show (for example fade in) when PhotoSwipe is opened
 */
.pswp .pswp__hide-on-close {
	opacity: 0.005;
	will-change: opacity;
	transition: opacity var(--pswp-transition-duration) cubic-bezier(0.4, 0, 0.22, 1);
	z-index: 10; /* always overlap slide content */
	pointer-events: none; /* hidden elements should not be clickable */
}

/* class pswp--ui-visible is added when opening or closing transition starts */
.pswp--ui-visible .pswp__hide-on-close {
	opacity: 1;
	pointer-events: auto;
}

/* <button> styles, including css reset */
.pswp__button {
	position: relative;
	display: block;
	width: 50px;
	height: 60px;
	padding: 0;
	margin: 0;
	overflow: hidden;
	cursor: pointer;
	background: none;
	border: 0;
	box-shadow: none;
	opacity: 0.85;
	-webkit-appearance: none;
	-webkit-touch-callout: none;
}

.pswp__button:hover,
.pswp__button:active,
.pswp__button:focus {
  transition: none;
  padding: 0;
  background: none;
  border: 0;
  box-shadow: none;
  opacity: 1;
}

.pswp__button:disabled {
  opacity: 0.3;
  cursor: auto;
}

.pswp__icn {
  fill: var(--pswp-icon-color);
  color: var(--pswp-icon-color-secondary);
}

.pswp__icn {
  position: absolute;
  top: 14px;
  left: 9px;
  width: 32px;
  height: 32px;
  overflow: hidden;
  pointer-events: none;
}

.pswp__icn-shadow {
  stroke: var(--pswp-icon-stroke-color);
  stroke-width: var(--pswp-icon-stroke-width);
  fill: none;
}

.pswp__icn:focus {
	outline: 0;
}

/*
	div element that matches size of large image,
	large image loads on top of it,
	used when msrc is not provided
*/
div.pswp__img--placeholder,
.pswp__img--with-bg {
	background: var(--pswp-placeholder-bg);
}

.pswp__top-bar {
	position: absolute;
	left: 0;
	top: 0;
	width: 100%;
	height: 60px;
	display: flex;
  flex-direction: row;
  justify-content: flex-end;
	z-index: 10;

	/* allow events to pass through top bar itself */
	pointer-events: none !important;
}
.pswp__top-bar > * {
  pointer-events: auto;
  /* this makes transition significantly more smooth,
     even though inner elements are not animated */
  will-change: opacity;
}


/*

  Close button

*/
.pswp__button--close {
  margin-right: 6px;
}


/*

  Arrow buttons

*/
.pswp__button--arrow {
  position: absolute;
  top: 0;
  width: 75px;
  height: 100px;
  top: 50%;
  margin-top: -50px;
}

.pswp__button--arrow:disabled {
  display: none;
  cursor: default;
}

.pswp__button--arrow .pswp__icn {
  top: 50%;
  margin-top: -30px;
  width: 60px;
  height: 60px;
  background: none;
  border-radius: 0;
}

.pswp--one-slide .pswp__button--arrow {
  display: none;
}

/* hide arrows on touch screens */
.pswp--touch .pswp__button--arrow {
  visibility: hidden;
}

/* show arrows only after mouse was used */
.pswp--has_mouse .pswp__button--arrow {
  visibility: visible;
}

.pswp__button--arrow--prev {
  right: auto;
  left: 0px;
}

.pswp__button--arrow--next {
  right: 0px;
}
.pswp__button--arrow--next .pswp__icn {
  left: auto;
  right: 14px;
  /* flip horizontally */
  transform: scale(-1, 1);
}

/*

  Zoom button

*/
.pswp__button--zoom {
  display: none;
}

.pswp--zoom-allowed .pswp__button--zoom {
  display: block;
}

/* "+" => "-" */
.pswp--zoomed-in .pswp__zoom-icn-bar-v {
  display: none;
}


/*

  Loading indicator

*/
.pswp__preloader {
  position: relative;
  overflow: hidden;
  width: 50px;
  height: 60px;
  margin-right: auto;
}

.pswp__preloader .pswp__icn {
  opacity: 0;
  transition: opacity 0.2s linear;
  animation: pswp-clockwise 600ms linear infinite;
}

.pswp__preloader--active .pswp__icn {
  opacity: 0.85;
}

@keyframes pswp-clockwise {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}


/*

  "1 of 10" counter

*/
.pswp__counter {
  height: 30px;
  margin-top: 15px;
  margin-inline-start: 20px;
  font-size: 14px;
  line-height: 30px;
  color: var(--pswp-icon-color);
  text-shadow: 1px 1px 3px var(--pswp-icon-color-secondary);
  opacity: 0.85;
}

.pswp--one-slide .pswp__counter {
  display: none;
}
.gallery-container{
    margin: 0;
    padding: 0;
    /* background-color: transparent; */
    font-family: 'Arial', sans-serif;
    height: 85vh;
    max-height: 900px;
    overflow: scroll;
    border: none;
}
.gallery-container:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #f7f7f7;
  opacity: 0.1;
  /* background-image:  linear-gradient(#626484 1.8px, transparent 1.8px), 
                     linear-gradient(90deg, #626484 1.8px, transparent 1.8px), 
                     linear-gradient(#626484 0.9px, transparent 0.9px), 
                     linear-gradient(90deg, #626484 0.9px, #e5e5f7 0.9px);
  background-size: 45px 45px, 45px 45px, 9px 9px, 9px 9px;
  background-position: -1.8px -1.8px, -1.8px -1.8px, -0.9px -0.9px, -0.9px -0.9px; */
  border-radius: 10px; /* Match border radius with parent */
  z-index: -1; /* Ensure it is behind the content */
}
.my-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 0.8fr));
    gap: 10px;
    padding: 10px;
}
.my-gallery a {
    display: flex;
    flex-direction: column;
    justify-content: flex-end; /* Align items to bottom but ensure flex properties apply correctly */
    align-items: center; /* Center align the items */
    border: 1px solid #ccc;
    border-radius: 8px;
    overflow: hidden;
    position: relative;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    height: 240px; /* Fixed height for uniformity */
}
.my-gallery a:hover {
    box-shadow: 0 8px 16px rgba(0,0,0,0.2);
    scale: 1.02;
    transition: all 0.5s;
}
.my-gallery img {
    width: 80%; /* Limit width but ensure center alignment */
    height: auto; /* Keep the height proportional */
    margin: auto; /* Center the image horizontally */
    align-self: center; /* Center align the image specifically */
}


.description {
    width: 100%;
    text-align: center;
    padding: 5px;
    background-color: #fff;
    border-top: 1px solid #ccc;
}
#filter-bar {

    background-color: #f1f3f4; 
    text-align: center;
    display: flex;
    align-items: center; /* Ensures all elements are vertically aligned in the center */
    justify-content: space-around;
    flex-wrap: nowrap; /* Prevents wrapping to ensure horizontal alignment */
    position: sticky;
    top: 0;
    z-index: 100;
    border-radius: 12px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.05); /* Updated shadow for a more subtle effect */
    border: 1px solid #d0d7de; /* Lighter border color for a modern look */
}

.filter-select {
    padding: 8px 12px;
    margin: 0 10px; /* Uniform margin for alignment */
    cursor: pointer;
    border: none;
    border-radius: 6px;
    appearance: none;
    background-color: #ffffff;
    background-image: url('data:image/svg+xml;utf8,<svg fill="%23333" height="20" viewBox="0 0 24 24" width="20" xmlns="http://www.w3.org/2000/svg"><path d="M7 10l5 5 5-5z"/></svg>'); /* Smaller and darker arrow for a sleek look */
    background-repeat: no-repeat;
    background-position: right 10px center;
    background-size: 20px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.1);
    transition: background-color 0.3s, box-shadow 0.3s;
}

.filter-select:hover {
    background-color: #e6e6e6; /* Tech-inspired hover color */
    box-shadow: 0 2px 4px rgba(0,0,0,0.15);
}

button#clear-filters {
    padding: 8px 20px;
    margin: 0 10px;
    cursor: pointer;
    border: none;
    border-radius: 6px;
    background-color: #007bff; /* Bright blue for a techy button */
    color: white;
    font-weight: bold; /* Makes the text stand out more */
    transition: background-color 0.3s;
}

button#clear-filters:hover {
    background-color: #0056b3; /* Deeper blue on hover */
}

.modal {
    display: none;
    position: absolute;
    z-index: 1001;
    left: 0;
    top: 0;
    border-radius: 10px;
    /* width: 100%;
    height: 100%; */
    overflow: auto;
    align-items: center;
    justify-content: center;
    background-color: rgb(0,0,0,0.9);

}
.modal-img-caption {
    /* background-color: grey; */
    height: 90%;
    width: 90%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 20px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
}

.modal-content {
    display: block;
    max-width: 90%;
    max-height: 70%;
    width: auto;
    height: auto;
    margin-bottom: 10px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -o-user-select: none;
  user-select: none;
}


.caption {
    max-width: 80%;
    /* max-width: 700px; */
    height: auto;
    white-space: initial;
    text-align: center;
    color: #333;
    font-size: 18px;
    padding: 10px;
    background-color: #f9f9f9;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.close {
    position: absolute;
    top: 15px;
    right: 35px;
    color: #f1f1f1;
    font-size: 40px;
    font-weight: bold;
    cursor: pointer;
}

@keyframes fadeInScaleUp {
  0% {
    opacity: 0;
    transform: scale(0.95);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}
@keyframes fadeOutScaleDown {
  0% {
    opacity: 1;
    transform: scale(1);
  }
  100% {
    opacity: 0;
    transform: scale(0.5);
  }
}

.hidden {
  visibility: hidden;
  opacity: 0;
  transition: visibility 0s 0.5s, opacity 0.5s linear; 
}

.visible {
  visibility: visible;
  opacity: 1;
  transition: opacity 0.5s linear; 
}
.fade-in{
 animation: fadeInScaleUp 0.5s ease-in-out forwards; 

}
.fade-out {
  animation: fadeOutScaleDown 0.5s ease-in-out forwards;
}


</style>



```js
/****************************************************************************
 * Hard-coded chart types (same as before)
 ****************************************************************************/
let visualizationTypes = [
  "Geometry", "Other", "Connection", "Sankey", "Scientific Viz", "Line Plot", 
  "Flow Chart", "Chord Diagram", "Complex Diagram", "Arc Diagram", 
  "Connected Scatter", "Circular Diagram", "Ridgeline", "Network", 
  "Circular Packing", "Table", "Barplot", "Scatter", "Geometric", 
  "Density", "Histogram", "Wordcloud", "Boxplot", "Density 2d", 
  "Bubble", "Heatmap", "Dendrogram", "Circuit Diagram", "Contour Plot", 
  "Error Bars Plot", "Error Bar Plot", "Surface Plot", "Hexbin Map", 
  "Timeline", "Map", "Choropleth", "Stacked Area", "Spider / Radar", 
  "Node Diagram", "Venn Diagram", "Correlogram", "Graph", "Violin", 
  "3D Surface Plot", "Diagram", "Vector Field", "Spectrum", "Bubble Map", 
  "Performance Diagram", "Radar", "Pie Chart", "Cluster visualization", 
  "Doughnut", "Other (if none of the above categories fit)", "Area", 
  "Cumulative completeness", "Polar Plot", "Matrix", "Schematic", "Parallel", 
  "3D", "Bipartite", "Lollipop", "Forest Plot", "3D Scatter", "Contour", 
  "Errorbar Plot", "Reconstructed OPD", "Horizontal Barplot", "Attention Map", 
  "Image", "3D Surface", "3D Plot", "Light Plot", "UMAP", "Circular Barplot", 
  "World model", "Phase Diagram", "Cumulative Distribution", "3D Barplot", 
  "Band Structure", "Ternary Plot", "Streamchart", "CDF", "Point Plot", 
  "Tree", "Photo", "Power Spectral Density", "Circle Diagram"
];

/****************************************************************************
 * 1) DuckDB setup & Queries
 ****************************************************************************/
import * as duckdb from "npm:@duckdb/duckdb-wasm";
const db = await DuckDBClient.of({base: FileAttachment("/data/new_layout_updated.db")});

// Query #1: Figures + Paper info
async function initialDB(db) {
  try {
    const results = await db.query(`
      SELECT 
        f.id AS figure_id,
        p.id AS paper_id,
        p.title,
        p.doi,
        p.publication_date,
        p.oa_url,
        p.pdf_path,
        p.inst_id,
        p.primary_topic_id,
        f.local_path,
        f.server_path,
        fp.name,
        fp.int_value AS ChartType,
        fp.string_value AS Something,
        fp.xPos,
        fp.yPos,
        fp.zPos
      FROM 
        base.figure f
      LEFT JOIN 
        base.paper p ON f.paper_id = p.id
      LEFT JOIN 
        base.figure_property fp ON f.id = fp.figure_id
      ORDER BY f.id;
    `);
    return results.toArray();
  } catch (error) {
    console.error("Error executing query:", error);
  }
}

// Query #2: Topics
async function countTopics(db) {
  try {
    const results = await db.query(`
      SELECT 
        id,
        name,
        subfield,
        field,
        domain
      FROM base.topic
    `);
    return results.toArray();
  } catch (error) {
    console.error("Error executing query:", error);
    throw error;
  }
}

// Grab topics & main data
const topicsArray = await countTopics(db);
const database = await initialDB(db);

// Utility to find a topic object by ID
function getObjectById(data, id) {
  return data.find(item => item.id === id);
}

// Hide loading once data is ready
document.getElementById("loading-overlay").style.display = "none";

/****************************************************************************
 * 2) GALLERY FUNCTION
 ****************************************************************************/
function gallery() {
  // DOM references
  const observableMain = document.getElementById('observablehq-main');
  const galleryElement = document.querySelector('.my-gallery');
  const galleryContainer = document.querySelector('.gallery-container');
  const label1Select = document.getElementById('label1-filter');
  const label2Select = document.getElementById('label2-filter');
  const clearFiltersBtn = document.getElementById('clear-filters');
  const modal = document.getElementById('myModal');
  const modalImg = document.getElementById('img01');
  const captionText = document.querySelector('.caption');
  const span = document.getElementsByClassName("close")[0];

  // If we have an 'observablehq-main', adjust modal size
  if (observableMain) {
    modal.style.width = `${galleryContainer.offsetWidth}px`;
    modal.style.height = `${galleryContainer.offsetHeight}px`;
  }

  // A) Create the full gallery from DB
  createGalleryItems(database);

  // B) Populate the filters initially
  populateFilter(label1Select, "primary_topic_id", database, "All");
  populateFilter(label2Select, "ChartType", database, "All");

  // C) “Smart” filter logic
  let isPopulating = false;
  label1Select.onchange = () => handleFilterChange("topic");
  label2Select.onchange = () => handleFilterChange("chart");

  // D) Clear button resets filters + re-populates
  clearFiltersBtn.onclick = () => {
    label1Select.value = "All";
    label2Select.value = "All";
    applyFilters();
    populateFilter(label1Select, "primary_topic_id", database, "All");
    populateFilter(label2Select, "ChartType", database, "All");
  };

  // E) Modal close logic
  span.onclick = () => { modal.style.display = "none"; };
  window.onclick = e => { if (e.target === modal) modal.style.display = "none"; };

  /**************************************************************************
   * createGalleryItems: clone the <template> for each row
   **************************************************************************/
  function createGalleryItems(items) {
    // Grab our template
    const template = document.getElementById('gallery-item-template');

    items.forEach(item => {
      // 1) Clone the template
      const clone = template.content.cloneNode(true);

      // 2) Grab references to the important elements
      const link = clone.querySelector('.gallery-item');
      const img = clone.querySelector('img.lazy-load');
      const descChart = clone.querySelector('.desc-chart');
      const descTopic = clone.querySelector('.desc-topic');
      const descTitle = clone.querySelector('.desc-title');

      // 3) Set dataset + text
      link.dataset.primary_topic_id = item.primary_topic_id;
      link.dataset.charttype = item.ChartType;

      const topicObj = getObjectById(topicsArray, item.primary_topic_id);
      const topicName = topicObj ? topicObj.name : "Unknown Topic";
      const chartLabel = visualizationTypes[item.ChartType] || `Chart #${item.ChartType}`;

      // For lazy loading
      img.dataset.src = item.server_path;
      // Fill text
      descChart.textContent = `Chart: ${chartLabel}`;
      descTopic.textContent = `Topic: ${topicName}`;
      descTitle.textContent = item.title;
      descTitle.title = item.title; // tooltip on hover

      // 4) Set background color based on ChartType
      setLinkBackground(link, item.ChartType);

      // 5) On click -> open modal
      link.onclick = e => {
        e.preventDefault();
        modal.style.display = "flex";
        modalImg.src = item.server_path;
        captionText.innerHTML = `
          <strong>Chart:</strong> ${chartLabel}<br/>
          ${item.Something ? `<strong>Detail:</strong> ${item.Something}<br/>` : ""}
          <a target="_blank" href="${item.doi}">${item.title}</a>
        `;
      };

      // 6) Append to the .my-gallery grid
      galleryElement.appendChild(clone);
    });

    // 7) Finally, lazy-load images
    initializeLazyLoading();
  }

  /**************************************************************************
   * setLinkBackground: dynamic color from chart type
   **************************************************************************/
  function setLinkBackground(linkElement, label) {
    const colors = [
      "#e6194B","#3cb44b","#ffe119","#4363d8","#f58231","#911eb4","#46f0f0","#f032e6",
      "#bcf60c","#fabebe","#008080","#e6beff","#9a6324","#fffac8","#800000","#aaffc3",
      "#808000","#ffd8b1","#000075","#808080","#fa8072","#4682b4","#6a5acd","#20b2aa",
      "#9400d3","#ff6347","#40e0d0","#ee82ee","#dda0dd","#b0c4de","#ff7f50","#6495ed",
      "#deb887","#5f9ea0","#7fff00","#d2691e","#ff69b4","#1e90ff","#228b22","#ffc0cb",
      "#8a2be2","#a52a2a","#8b008b","#b8860b","#66cdaa","#ff4500","#daa520","#98fb98",
      "#afeeee","#db7093"
    ];
    if (label >= 0 && label < colors.length) {
      const color = colors[label];
      const r = parseInt(color.slice(1,3), 16);
      const g = parseInt(color.slice(3,5), 16);
      const b = parseInt(color.slice(5,7), 16);
      linkElement.style.backgroundColor = `rgba(${r},${g},${b},0.2)`;
    } else {
      linkElement.style.backgroundColor = 'transparent';
    }
  }

  /**************************************************************************
   * initializeLazyLoading
   **************************************************************************/
  function initializeLazyLoading() {
    const lazyImages = document.querySelectorAll('.lazy-load');
    const observer = new IntersectionObserver((entries, obs) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const image = entry.target;
          image.src = image.dataset.src; // load real source
          obs.unobserve(image);
        }
      });
    });
    lazyImages.forEach(img => observer.observe(img));
  }

  /**************************************************************************
   * populateFilter: fill a <select> with unique values from data
   **************************************************************************/
  function populateFilter(selectElement, labelType, dataArray, currentSelection) {
    // Gather unique IDs
    const labelSet = new Set();
    dataArray.forEach(item => {
      const val = item[labelType];
      if (val !== null && val !== undefined) labelSet.add(val);
    });
    const sortedVals = Array.from(labelSet).sort((a,b)=>a-b);

    // Clear existing
    while (selectElement.firstChild) {
      selectElement.removeChild(selectElement.firstChild);
    }

    // Add "All"
    const allOpt = document.createElement('option');
    allOpt.value = "All";
    allOpt.text = "All";
    selectElement.appendChild(allOpt);

    // Add each unique val
    sortedVals.forEach(v => {
      const opt = document.createElement('option');
      opt.value = v;
      if (labelType === "ChartType") {
        opt.text = visualizationTypes[v] || `Chart #${v}`;
      } else {
        const tObj = getObjectById(topicsArray, v);
        opt.text = tObj ? tObj.name : `Topic #${v}`;
      }
      selectElement.appendChild(opt);
    });

    // Keep old selection if valid
    if (currentSelection !== "All" && sortedVals.map(String).includes(currentSelection)) {
      selectElement.value = currentSelection;
    } else {
      selectElement.value = "All";
    }
  }

  /**************************************************************************
   * handleFilterChange: "smart" filter logic
   **************************************************************************/
  function handleFilterChange(changed) {
    if (isPopulating) return;
    isPopulating = true;

    const selectedTopic = label1Select.value;
    const selectedChart = label2Select.value;

    let subset = database;
    if (changed === "topic") {
      // If topic != All, filter to that topic
      if (selectedTopic !== "All") {
        subset = database.filter(d => String(d.primary_topic_id) === selectedTopic);
      }
      // Re-populate chart filter with subset
      populateFilter(label2Select, "ChartType", subset, selectedChart);

    } else if (changed === "chart") {
      // If chart != All, filter to that chart
      if (selectedChart !== "All") {
        subset = database.filter(d => String(d.ChartType) === selectedChart);
      }
      // Re-populate topic filter with subset
      populateFilter(label1Select, "primary_topic_id", subset, selectedTopic);
    }

    applyFilters();
    isPopulating = false;
  }

  /**************************************************************************
   * applyFilters: show/hide + optional sorting
   **************************************************************************/
  function applyFilters() {
    const selectedTopic = label1Select.value;
    const selectedChart = label2Select.value;
    const links = Array.from(galleryElement.querySelectorAll('.gallery-item'));

    // Show/hide
    links.forEach(link => {
      const t = link.dataset.primary_topic_id;
      const c = link.dataset.charttype;
      let visible = true;
      if (selectedTopic !== "All" && t !== selectedTopic) visible = false;
      if (selectedChart !== "All" && c !== selectedChart) visible = false;
      link.style.display = visible ? 'flex' : 'none';
    });

    // Sort if only one filter chosen
    let visibleLinks = links.filter(l => l.style.display === 'flex');
    if (selectedTopic !== "All" && selectedChart === "All") {
      // Sort by chart
      visibleLinks.sort((a,b)=>{
        const aC = parseInt(a.dataset.charttype)||0;
        const bC = parseInt(b.dataset.charttype)||0;
        return aC - bC;
      });
    } else if (selectedTopic === "All" && selectedChart !== "All") {
      // Sort by topic
      visibleLinks.sort((a,b)=>{
        const aT = parseInt(a.dataset.primary_topic_id)||0;
        const bT = parseInt(b.dataset.primary_topic_id)||0;
        return aT - bT;
      });
    }
    // If both are "All" or both specific, no special sorting

    // Re-append in sorted order
    visibleLinks.forEach(link => galleryElement.appendChild(link));
  }
}

// 3) Finally, run the gallery
gallery();

```


<template id="gallery-item-template">
  <a class="gallery-item" href="#">
    <img class="lazy-load" alt="Figure Image" />
    <div class="description">
      <div class="description-content">
        <div class="desc-chart"></div>
        <div class="desc-topic"></div>
        <div class="desc-title"></div>
      </div>
    </div>
  </a>
</template>

<!-- Loading Overlay (initially visible) -->
<div id="loading-overlay">
  <div class="loader"></div>
  <p>Loading data...</p>
</div>

<div class="gallery-container card">
  <div id="filter-bar">
    <div id="topic">Topic: 
      <select id="label1-filter" class="filter-select">
        <option>All</option>
      </select>
    </div>
    <div id="chart">Chart:
      <select id="label2-filter" class="filter-select">
        <option>All</option>
      </select>
    </div>
    <button id="clear-filters">Clear Filters</button>
  </div>

  <div class="my-gallery" itemscope itemtype="http://schema.org/ImageGallery"></div>

  <div id="myModal" class="modal">
    <div class="modal-img-caption">
      <span class="close">&times;</span>
      <img class="modal-content" id="img01">
      <div class="caption"></div>
    </div>
  </div>
</div>
