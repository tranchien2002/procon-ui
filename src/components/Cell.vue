<template>
<<<<<<< HEAD
  <div class="cell" v-bind:style="{ backgroundColor: color}">
    {{this.agentID}}
    <br />
    {{this.cellData}}
    <!-- <br />
    {{this.tiled[this.y][x]}}-->
=======
  <div class="cell">
    <!-- <div class="content" v-show="isValueVisible">{{ value }}</div> -->
>>>>>>> e29db0f4e08f21de83a678e845d605ded7bcffff
  </div>
</template>

<script>
export default {
  props: {
<<<<<<< HEAD
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
=======
    cellData: Object
    // bombIcon: {
    //   type: String,
    //   default: "💣"
    // },
    // flagIcon: {
    //   type: String,
    //   default: "❗"
    // }
>>>>>>> e29db0f4e08f21de83a678e845d605ded7bcffff
  },
  data() {
    return {};
  },
<<<<<<< HEAD
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
=======
  methods: {
    onCellLeftClicked() {
      this.$emit("onCellLeftClicked", {
        x: this.cellData.x,
        y: this.cellData.y
      });
    },
    onCellRightClicked() {
      this.$emit("onCellRightClicked", {
        x: this.cellData.x,
        y: this.cellData.y
      });
    }
  },
  computed: {
    value() {
      // Revealed can be a bomb or a number
      if (this.isRevealed) {
        if (this.cellData.isBomb) {
          return this.bombIcon;
        } else {
          return this.cellData.proximityCount > 0
            ? this.cellData.proximityCount
            : "";
        }
      }
      // Unrevealed is marked or empty
      return this.cellData.isMarked ? this.flagIcon : "";
    },
    isValueVisible() {
      return this.isRevealed || this.cellData.isMarked;
    },
    isRevealed() {
      return this.cellData.isRevealed;
>>>>>>> e29db0f4e08f21de83a678e845d605ded7bcffff
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
<<<<<<< HEAD
  min-width: 60px;
  max-width: 60px;
  max-height: 35px;
  min-height: 35px;
=======
  min-width: 24px;
  max-width: 40px;
>>>>>>> e29db0f4e08f21de83a678e845d605ded7bcffff
  border: #ddd 1px solid;
}

// Equal the height to the cell's width
.cell:before {
  content: "";
  display: block;
<<<<<<< HEAD
  padding-top: 10%; /* initial ratio of 1:1*/
=======
  padding-top: 100%; /* initial ratio of 1:1*/
>>>>>>> e29db0f4e08f21de83a678e845d605ded7bcffff
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