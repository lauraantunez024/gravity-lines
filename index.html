<!DOCTYPE html>
<meta charset="utf-8">
<link rel="stylesheet" href="styles/main.css">
<link rel="stylesheet" href="//rawgithub.com/Caged/d3-tip/master/examples/example-styles.css">
<style>
svg {
  font: 10px sans-serif;
}
.x.axis .domain {
  fill: none;
  stroke: #000;
  shape-rendering: crispEdges;
}
.x.axis path {
  fill: none;
  stroke: #000;
  opacity: .2;
  shape-rendering: crispEdges;
}
  @font-face {
      font-family: 'Times New Roman';
      src: url('fonts/Times New Roman-Light.woff');
      font-weight: 200;
      font-style: normal;
    }
    @font-face {
      font-family: 'Times New Roman';
      src: url('fonts/Times New Roman-Thin.woff');
      font-weight: 100;
      font-style: normal;
    }
    @font-face {
      font-family: 'Times New Roman';
      src: url('fonts/Times New Roman-Regular.woff');
      font-weight: 300;
      font-style: normal;
    }
    @font-face {
      font-family: 'Times New Roman';
      src: url('fonts/Times New Roman-Black.woff');
      font-weight: 900;
      font-style: normal;
    }
    @font-face {
      font-family: 'Times New Roman';
      src: url('fonts/Times New Roman-Bold.woff');
      font-weight: 700;
      font-style: normal;
    }
    @font-face {
      font-family: 'Tiempos';
      src: url('fonts/TiemposText-Regular.woff');
      font-weight: 300;
      font-style: normal;
    }
}

.tick {
  font-family: Times New Roman;
}

</style>
<body>
    <div class="main-content">
  <div class="total">
      <div class="constrict">
        <section class="content main-graphics">
            </div>
              <div class="hed">Changing housing market in South Carolina Nov. 2020 to Nov.2021</div>
              <div class="dek">Data from South Carolina Realtors Annual Report</div>
            </section>
          </div></div></div>

<script src="https://d3js.org/d3.v3.min.js"></script>
<script src="./d3-tip.js"></script>
<script>

var margin = {top: 50, right: 50, bottom: 30, left: 50},
    width = 460 - margin.left - margin.right,
    height = 120 - margin.top - margin.bottom,
    // padding between nodes
    padding = 1,
    maxRadius = 1000,
    numberOfNodes = 50;

var colorize = d3.scale.linear().domain([0,50,100])
  .range(["#3159A0", "#244DE4","purple"])

// Create random node data.
// var dater = d3.range(numberOfNodes).map(function() {
//   var value = Math.floor(Math.random() * 50) / 10,
//       size = Math.floor( Math.sqrt((value + 1) / numberOfNodes * -Math.log(Math.random())) * maxRadius * 10 ),
//       datum = {value: value, size: size};
//   return datum;
// });





var x = d3.scale.linear()
  .domain( [0, 100] )
  .range( [margin.left, width + margin.right ] );

d3.csv("data.csv", function(error, data){

// Map the basic node data to d3-friendly format.
var nodes = data.map(function(node, index) {
  return {
    label: node.county,
    class: node.class,
    fig: node.dataPrice,
    idealradius: 700 / 100,
    radius: 0,
    // Give each node a random color.
    color: '#ff7f0e',
    // Set the node's gravitational centerpoint.
    idealcx: x(+node.dataPrice),
    idealcy: height,
    x: x(+node.dataPrice),
    // Add some randomization to the placement;
    // nodes stacked on the same point can produce NaN errors.
    y: height / .5 + Math.random()
  };
});

var force = d3.layout.force()
  .nodes(nodes)
  .size([width, height])
  .gravity(0)
  .charge(0)
  .on("tick", tick)
  .start();

var xAxis = d3.svg.axis()
  .scale(x);

var svg = d3.select("body").append("svg")
  .attr("width", width + margin.left + margin.right)
  .attr("height", height + margin.top + margin.bottom);

var title = svg.append("text")
  .classed("title", true)
  .attr("x", 42)
  .attr("y", 12)
  .style("text-anchor", "start")
  .attr("font-family", "Times New Roman")
      .attr("font-size", 16)
  .text("Price % increase of homes, villas and condos");

var tipText = svg.append("text")
      .classed("tip-text", true)
      .attr("x", width/2 + 40 )
      .attr("y", 50)
      .attr("dy", "1.35em")
      .attr("dx", ".45em")
      .style("text-anchor", "middle")
      .style("fill", "black")
      .style("opacity", "1")
      .attr('transform', function(d) {
        return 'translate(0, 0)'
      })
      .attr("font-family", "Times New Roman")
      .attr("font-size", 24)
      .text("");

var loading = svg.append("text")
  .attr("x", ( width + margin.left + margin.right ) / 2)
  .attr("y", ( height + margin.top + margin.bottom ) / 2)
  .attr("dy", ".35em")
  .style("text-anchor", "middle")
  .text("Simulating. One moment please…");

/**
 * On a tick, apply custom gravity, collision detection, and node placement.
 */
function tick(e) {
  for ( i = 0; i < nodes.length; i++ ) {
    var node = nodes[i];
    /*
     * Animate the radius via the tick.
     *
     * Typically this would be performed as a transition on the SVG element itself,
     * but since this is a static force layout, we must perform it on the node.
     */
    node.radius = node.idealradius - node.idealradius * e.alpha * 10;
    node = gravity(.2 * e.alpha)(node);
    node = collide(.5)(node);
    node.cx = node.x;
    node.cy = node.y;
  }
}

/**
 * On a tick, move the node towards its desired position,
 * with a preference for accuracy of the node's x-axis placement
 * over smoothness of the clustering, which would produce inaccurate data presentation.
 */
function gravity(alpha) {
  return function(d) {
    d.y += (d.idealcy - d.y) * alpha;
    d.x += (d.idealcx - d.x) * alpha * 3;
    return d;
  };
}

/**
 * On a tick, resolve collisions between nodes.
 */
function collide(alpha) {
  var quadtree = d3.geom.quadtree(nodes);
  return function(d) {
    var r = d.radius + maxRadius + padding,
        nx1 = d.x - r,
        nx2 = d.x + r,
        ny1 = d.y - r,
        ny2 = d.y + r;
    quadtree.visit(function(quad, x1, y1, x2, y2) {
      if (quad.point && (quad.point !== d)) {
        var x = d.x - quad.point.x,
            y = d.y - quad.point.y,
            l = Math.sqrt(x * x + y * y),
            r = d.radius + quad.point.radius + padding;
        if (l < r) {
          l = (l - r) / l * alpha;
          d.x -= x *= l;
          d.y -= y *= l;
          quad.point.x += x;
          quad.point.y += y;
        }
      }
      return x1 > nx2 || x2 < nx1 || y1 > ny2 || y2 < ny1;
    });
    return d;
  };
}

/**
 * Run the force layout to compute where each node should be placed,
 * then replace the loading text with the graph.
 */
function renderGraph() {
  // Run the layout a fixed number of times.
  // The ideal number of times scales with graph complexity.
  // Of course, don't run too long—you'll hang the page!
  force.start();
  for (var i = 100; i > 0; --i) force.tick();
  force.stop();

  svg.append("g")
    .attr("class", "x axis")
    .attr("transform", "translate(0," + ( height )  + ")")
    .call(xAxis.ticks(1).tickFormat((d)=>{
      return d+ "%"
    }).tickSize(0));


  var circle = svg.selectAll("circle")
    .data(nodes)
  .enter().append("circle").attr("class",(d)=>{ return d.class.toLowerCase() })
    .style("fill", d => colorize(d.fig))
    .attr("cx", function(d) { return d.x} )
    .attr("cy", function(d) { return d.y} )
    .attr("r", function(d) { return d.radius} )
    .attr("opacity", .7)
    .on('mouseover', function(e) {
      var selecta = "." + e.class.toLowerCase();
      d3.selectAll("circle")
        .transition()
        .duration(100)
        .attr("opacity", .2)

      d3.selectAll(selecta)
        .transition()
        .duration(100)
        .attr("opacity", 1)
      tipText
          .text(()=>{
            return e.label
          })
      tipText
        .transition()
        .duration(100)
        .style("opacity", .6)
    })
          .on('mouseout', function(e) {
              d3.selectAll("circle")
                .transition()
                .duration(100)
                .attr("opacity", .7)      
      tipText
        .transition()
        .duration(100)
        .style("opacity", 0)
    });

  loading.remove();
}
setTimeout(renderGraph, 10);
});

d3.csv("data.csv", function(error, data){

// Map the basic node data to d3-friendly format.
var nodes = data.map(function(node, index) {
  return {
    label: node.county,
    class: node.class,
    fig: node.data,
    idealradius: 700 / 100,
    radius: 0,
    // Give each node a random color.
    color: '#ff7f0e',
    // Set the node's gravitational centerpoint.
    idealcx: x(+node.data),
    idealcy: height,
    x: x(+node.data),
    // Add some randomization to the placement;
    // nodes stacked on the same point can produce NaN errors.
    y: height / 2 + Math.random()
  };
});

var force = d3.layout.force()
  .nodes(nodes)
  .size([width, height])
  .gravity(0)
  .charge(0)
  .on("tick", tick)
  .start();

var xAxis = d3.svg.axis()
  .scale(x);

var svg = d3.select("body").append("svg")
  .attr("width", width + margin.left + margin.right)
  .attr("height", height + margin.top + margin.bottom);
var tipText = svg.append("text")
      .classed("tip-text", true)
      .attr("x", width/2 + 40 )
      .attr("y", 50)
      .attr("dy", "1.35em")
      .attr("dx", ".45em")
      .style("text-anchor", "middle")
      .style("fill", "black")
      .style("opacity", "1")
      .attr('transform', function(d) {
        return 'translate(0, 0)'
      })
      .attr("font-family", "Times New Roman")
      .attr("font-size", 24)
      .text("");
var title = svg.append("text")
  .classed("title", true)
  .attr("x", 42)
  .attr("y", 12)
  .style("text-anchor", "start")
  .attr("font-family", "Times New Roman")
      .attr("font-size", 16)
  .text("percent change of average days on market before sale");

var loading = svg.append("text")
  .attr("x", ( width + margin.left + margin.right ) / 2)
  .attr("y", ( height + margin.top + margin.bottom ) / 2)
  .attr("dy", ".35em")
  .style("text-anchor", "middle")
  .text("Simulating. One moment please…");

/**
 * On a tick, apply custom gravity, collision detection, and node placement.
 */
function tick(e) {
  for ( i = 0; i < nodes.length; i++ ) {
    var node = nodes[i];
    /*
     * Animate the radius via the tick.
     *
     * Typically this would be performed as a transition on the SVG element itself,
     * but since this is a static force layout, we must perform it on the node.
     */
    node.radius = node.idealradius - node.idealradius * e.alpha * 10;
    node = gravity(.2 * e.alpha)(node);
    node = collide(.5)(node);
    node.cx = node.x;
    node.cy = node.y;
  }
}

/**
 * On a tick, move the node towards its desired position,
 * with a preference for accuracy of the node's x-axis placement
 * over smoothness of the clustering, which would produce inaccurate data presentation.
 */
function gravity(alpha) {
  return function(d) {
    d.y += (d.idealcy - d.y) * alpha;
    d.x += (d.idealcx - d.x) * alpha * 3;
    return d;
  };
}

/**
 * On a tick, resolve collisions between nodes.
 */
function collide(alpha) {
  var quadtree = d3.geom.quadtree(nodes);
  return function(d) {
    var r = d.radius + maxRadius + padding,
        nx1 = d.x - r,
        nx2 = d.x + r,
        ny1 = d.y - r,
        ny2 = d.y + r;
    quadtree.visit(function(quad, x1, y1, x2, y2) {
      if (quad.point && (quad.point !== d)) {
        var x = d.x - quad.point.x,
            y = d.y - quad.point.y,
            l = Math.sqrt(x * x + y * y),
            r = d.radius + quad.point.radius + padding;
        if (l < r) {
          l = (l - r) / l * alpha;
          d.x -= x *= l;
          d.y -= y *= l;
          quad.point.x += x;
          quad.point.y += y;
        }
      }
      return x1 > nx2 || x2 < nx1 || y1 > ny2 || y2 < ny1;
    });
    return d;
  };
}

/**
 * Run the force layout to compute where each node should be placed,
 * then replace the loading text with the graph.
 */
function renderGraph() {
  // Run the layout a fixed number of times.
  // The ideal number of times scales with graph complexity.
  // Of course, don't run too long—you'll hang the page!
  force.start();
  for (var i = 100; i > 0; --i) force.tick();
  force.stop();

  svg.append("g")
    .attr("class", "x axis")
    .attr("transform", "translate(0," + ( height )  + ")")
    .call(xAxis.ticks(1).tickFormat((d)=>{
      return d+ "%"
    }).tickSize(0));

  var circle = svg.selectAll("circle")
    .data(nodes)
  .enter().append("circle").attr("class",(d)=>{ return d.class.toLowerCase() })
    .style("fill", d => colorize(d.fig))
    .attr("cx", function(d) { return d.x} )
    .attr("cy", function(d) { return d.y} )
    .attr("r", function(d) { return d.radius} )
    .attr("opacity", .7)
    .on('mouseover', function(e) {
      var selecta = "." + e.class.toLowerCase();
      d3.selectAll("circle")
        .transition()
        .duration(100)
        .attr("opacity", .2)

      d3.selectAll(selecta)
        .transition()
        .duration(100)
        .attr("opacity", 1)
      tipText
          .text(()=>{
            return e.label
          })
      tipText
        .transition()
        .duration(100)
        .style("opacity", .6)
    })
          .on('mouseout', function(e) {
              d3.selectAll("circle")
                .transition()
                .duration(100)
                .attr("opacity", .7)

      tipText
        .transition()
        .duration(100)
        .style("opacity", 0)
    });

  loading.remove();
}
setTimeout(renderGraph, 20);
});


// Use a timeout to allow the rest of the page to load first.


</script>
