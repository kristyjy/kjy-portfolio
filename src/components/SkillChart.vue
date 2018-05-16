<template>
  <svg ref="svg"></svg>
</template>

<script>
import * as d3 from 'd3';

export default {
  name: 'SkillChart',
  data() {
    return {
      skills: {
        children: [
          {
            label: 'HTML5',
            size: 550,
            color: 'rgba(255, 86, 124, 1)'
          },
          {
            label: 'CSS3',
            size: 600,
            color: '#85c6bf'
          },
          {
            label: 'JavaScript',
            size: 500,
            color: '#777'
          },
          {
            label: 'VueJS',
            size: 300,
            color: '#777'
          },
          {
            label: 'ReactJS',
            size: 400,
            color: '#cc4562'
          },
          {
            label: 'Redux',
            size: 400,
            color: '#cc4562'
          },
          {
            label: 'VueX',
            size: 300,
            color: 'rgba(255, 86, 124, 1)'
          },
          {
            label: 'Webpack',
            size: 200,
            color: '#cc4562'
          },
          {
            label: 'Sketch',
            size: 200,
            color: 'rgba(255, 86, 124, 1)'
          },
          {
            label: 'Gulp',
            size: 100,
            color: '#77ada7'
          },
          {
            label: 'Jekyll',
            size: 150,
            color: '#cc4562'
          },
          {
            label: 'Babel',
            size: 150,
            color: '#777'
          },
          {
            label: 'BEM',
            size: 150,
            color: '#77ada7'
          },
          {
            label: 'PostCSS',
            size: 100,
            color: '#85c6bf'
          },
          {
            label: 'SCSS',
            size: 100,
            color: '#77ada7'
          }
        ]
      },
      width: 300,
      height: 300
    }
  },
  methods: {
    renderChart() {
      var color = d3.scaleOrdinal(d3.schemeCategory20);

      var bubble = d3.pack(this.skills)
          .size([this.width, this.height])
          .padding(2);

      var svg = d3.select(this.$refs.svg)
          .html("")
          .attr("width", this.width)
          .attr("height", this.height)
          .attr("class", "bubble");

      var nodes = d3.hierarchy(this.skills)
          .sum(function(d) { return d.size; });

      var node = svg.selectAll(".node")
          .data(bubble(nodes).descendants())
          .enter()
          .filter(function(d){
            return !d.children
          })
          .append("g")
          .attr("class", "node")
          .attr("transform", function(d) {
            return "translate(" + d.x + "," + d.y + ")";
          });

      node.append("title")
          .text(function(d) {
            return d.data.label;
          });

      node.append("circle")
          .attr("r", function(d) {
              return d.r;
          })
          .style("fill", function(d,i) {
              return d.data.color;
          });

      node.append("text")
          .attr("dy", ".4em")
          .style("text-anchor", "middle")
          .text(function(d) {
            return d.data.label.substring(0, d.r / 3);
          })
          .attr("font-family",  "Open Sans")
          .attr("font-size", function(d){
              return d.r/3;
          })
          .attr("fill", "white");

      d3.select(self.frameElement)
          .style("height", this.height + "px");
    },
    onResize() {
      this.width = window.innerWidth;
      if (window.innerWidth < window.innerHeight * .8) {
        this.height = window.innerWidth;
      }
      else {
        this.height = window.innerHeight * .8;
      }
      this.renderChart();
    }
  },
  mounted() {
    this.onResize();
    window.addEventListener('resize', this.onResize, false);
  }
}
</script>

<style scoped>
svg {
  width: 100%;
  height: auto;
  display: block;
}
</style>
