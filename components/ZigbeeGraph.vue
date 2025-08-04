<script setup>
import * as d3 from 'd3'
import { onMounted, ref } from 'vue'

const svgRef = ref(null)

onMounted(() => {
  const nodes = [
    { id: "Coordinator", group: "coordinator" },
    { id: "Router 1", group: "router" },
    { id: "Router 2", group: "router" },
    { id: "Router 3", group: "router" },
    { id: "Router 4", group: "router" },
    { id: "End Device 1", group: "end" },
    { id: "End Device 2", group: "end" },
    { id: "End Device 3", group: "end" },
    { id: "End Device 4", group: "end" },
    { id: "End Device 5", group: "end" },
    { id: "End Device 6", group: "end" },
    { id: "End Device 7", group: "end" },
    { id: "End Device 8", group: "end" },
  ]

  const links = [
    { source: "Coordinator", target: "Router 1" },
    { source: "Coordinator", target: "Router 2" },
    { source: "Coordinator", target: "Router 3" },
    { source: "Router 1", target: "End Device 1" },
    { source: "Router 1", target: "End Device 2" },
    { source: "Router 2", target: "End Device 3" },
    { source: "Router 2", target: "End Device 4" },
    { source: "Router 3", target: "End Device 5" },
    { source: "Router 3", target: "End Device 6" },
    { source: "Router 2", target: "Router 4" },
    { source: "Router 4", target: "End Device 7" },
    { source: "Router 4", target: "End Device 8" },
  ]

  const color = {
    coordinator: "#e74c3c",
    router: "#e67e22",
    end: "#2ecc71",
  }

  const svg = d3.select(svgRef.value)
    .attr("width", 600)
    .attr("height", 600)
    .attr("viewBox", "0 0 600 600")

  const simulation = d3.forceSimulation(nodes)
    .force("link", d3.forceLink(links).id(d => d.id).distance(90))
    .force("charge", d3.forceManyBody().strength(-300))
    .force("center", d3.forceCenter(300, 300))
    .force("collision", d3.forceCollide().radius(25))

  const link = svg.append("g")
    .selectAll("line")
    .data(links)
    .join("line")
    .attr("stroke", "#999")

  const node = svg.append("g")
    .selectAll("circle")
    .data(nodes)
    .join("circle")
    .attr("r", 10)
    .attr("fill", d => color[d.group])

  // Add background rectangles for labels
  const labelBg = svg.append("g")
    .selectAll("rect")
    .data(nodes)
    .join("rect")
    .attr("width", d => d.id.length * 7 + 8)
    .attr("height", 16)
    .attr("rx", 3)
    .attr("fill", "rgba(255, 255, 255, 0.8)")
    .attr("stroke", "rgba(0, 0, 0, 0.1)")
    .attr("stroke-width", 0.5)

  const label = svg.append("g")
    .selectAll("text")
    .data(nodes)
    .join("text")
    .text(d => d.id)
    .attr("dy", -15)
    .attr("text-anchor", "middle")
    .attr("font-size", "12px")

  simulation.on("tick", () => {
    // Constrain nodes to stay within SVG bounds
    nodes.forEach(d => {
      d.x = Math.max(50, Math.min(550, d.x))
      d.y = Math.max(50, Math.min(550, d.y))
    })

    link
      .attr("x1", d => d.source.x)
      .attr("y1", d => d.source.y)
      .attr("x2", d => d.target.x)
      .attr("y2", d => d.target.y)

    node
      .attr("cx", d => d.x)
      .attr("cy", d => d.y)

    labelBg
      .attr("x", d => d.x - (d.id.length * 7 + 8) / 2)
      .attr("y", d => d.y - 28)

    label
      .attr("x", d => d.x)
      .attr("y", d => d.y)
  })
})
</script>

<template>
  <div class="flex justify-center">
    <svg ref="svgRef" width="100%" height="100%" viewBox="0 0 600 600" preserveAspectRatio="xMidYMid meet"></svg>
  </div>
</template>
