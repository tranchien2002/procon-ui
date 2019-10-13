<template>
  <div class="cell" v-bind:style="{ backgroundColor: color}">
    {{this.agentID}}
    <br />
    {{this.cellData}}
    <!-- <br />
    {{this.tiled[this.y][x]}}-->
  </div>
</template>

<script>
export default {
  props: {
    cellData: {
      type: Number
    },
    team: Array,
    x: {
      type: Number
    },
    y: {
      type: Number
    },
    tiled: {
      Array
    }
  },
  data() {
    return {};
  },
  methods: {},
  computed: {
    color: function() {
      if (this.tiled[this.y][this.x] == this.team[0].teamID) {
        return "GreenYellow";
      } else if (this.tiled[this.y][this.x] == this.team[1].teamID) {
        return "Bisque";
      } else {
        return;
      }
    },
    agentID: function() {
      // console.log(this.team[0].agents.length);
      for (let i in this.team[0].agents) {
        if (
          this.team[0].agents[i].x - 1 == this.x &&
          this.team[0].agents[i].y - 1 == this.y
        ) {
          return this.team[0].agents[i].agentID;
        }
      }

      for (let i in this.team[1].agents) {
        if (
          this.team[1].agents[i].x - 1 == this.x &&
          this.team[1].agents[i].y - 1 == this.y
        ) {
          return this.team[1].agents[i].agentID;
        }
      }
    }
  }
};
</script>

<style lang="scss">
.cell {
  // table-cell causes the cells to be of equal width in the row
  display: table-cell;
  position: relative;
  background-color: #eee;
  font-weight: bold;
  min-width: 60px;
  max-width: 60px;
  max-height: 35px;
  min-height: 35px;
  border: #ddd 1px solid;
}

// Equal the height to the cell's width
.cell:before {
  content: "";
  display: block;
  padding-top: 10%; /* initial ratio of 1:1*/
}

.content {
  // Ignore padding
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  // Center content
  display: flex;
  justify-content: center;
  align-items: center;
}

.revealed {
  background-color: #fff;
}
</style>