<template>
  <div id="app">
    <b-container class="bv-example-row">
      <b-row>
        <b-col>
          <b-form @submit="onSubmit" v-if="show">
            <b-form-group id="input-group-2" label="Host:" label-for="input-2">
              <b-form-input id="input-2" v-model="form.host" required placeholder="Enter host"></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-2" label="Token:" label-for="input-2">
              <b-form-input id="input-2" v-model="form.token" required placeholder="Enter token"></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-2" label="Match ID:" label-for="input-2">
              <b-form-input
                id="input-2"
                v-model="form.matchID"
                required
                placeholder="Enter matchID"
              ></b-form-input>
            </b-form-group>

            <label for="textarea-small">Input:</label>
            <b-form-textarea
              label="Text: "
              id="textarea"
              v-model="form.input"
              placeholder="Enter something..."
              rows="3"
              max-rows="6"
            ></b-form-textarea>
            <br>
            <b-button type="submit" variant="primary">Submit</b-button>
            <br>
            <br>
            <br>
            <label for="textarea-small">Response:</label>
            <b-form-textarea
              label="Text: "
              id="textareares"
              v-model="res"
              placeholder="Enter something..."
              rows="8"
              max-rows="12"
            ></b-form-textarea>
          </b-form>
        </b-col>
        <b-col>
          <div>
            <div v-for="(item, index1) in res.points" v-bind:key="index1">
              <Cell
                v-for="(i, index) in item"
                v-bind:key="index"
                v-bind:cellData="i"
                v-bind:team="res.teams"
                v-bind:x="index"
                v-bind:y="index1"
                v-bind:tiled="res.tiled"
              />
            </div>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Cell from "./components/Cell.vue";
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
export default {
  name: "app",
  components: {
    Cell
  },
  data() {
    return {
      form: {
        email: "",
        name: "",
        input: "",
        checked: []
      },
      res: JSON.parse(
        '{"turn":331,"teams":[{"agents":[{"x":16,"y":8,"agentID":1},{"x":10,"y":6,"agentID":2},{"x":1,"y":2,"agentID":3},{"x":2,"y":10,"agentID":4},{"x":16,"y":10,"agentID":5},{"x":8,"y":15,"agentID":6}],"teamID":217,"areaPoint":3,"tilePoint":27},{"agents":[{"x":13,"y":6,"agentID":7},{"x":8,"y":5,"agentID":8},{"x":1,"y":10,"agentID":9},{"x":10,"y":13,"agentID":10},{"x":1,"y":13,"agentID":11},{"x":11,"y":14,"agentID":12}],"teamID":251,"areaPoint":0,"tilePoint":36}],"tiled":[[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[217,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],[217,217,217,217,217,217,217,217,217,0,251,0,0,0,0,0],[217,217,217,0,0,0,217,217,0,217,251,0,0,0,0,0],[0,217,0,217,0,0,0,251,251,251,251,251,251,251,251,0],[0,0,217,0,217,217,217,217,217,217,0,217,251,0,0,0],[0,0,0,251,0,0,0,0,0,217,0,0,217,0,0,0],[0,0,251,0,0,0,0,0,0,0,217,0,0,0,0,217],[0,251,0,0,0,0,0,0,0,0,0,217,217,217,217,217],[251,217,217,217,0,0,0,0,0,0,0,0,251,0,0,217],[0,0,0,0,0,0,0,0,0,0,0,251,0,217,0,217],[0,251,0,0,0,0,0,0,0,0,251,0,0,0,217,217],[251,0,0,0,0,0,0,0,0,251,0,0,0,0,0,217],[217,217,217,217,217,217,0,0,0,0,251,0,0,0,0,0],[0,217,217,217,217,217,217,217,0,0,0,0,0,0,0,0],[0,0,217,0,0,0,0,0,0,0,0,0,0,0,0,0]],"width":16,"height":16,"points":[[16,13,10,7,3,5,3,7,7,3,5,3,7,10,13,16],[13,-10,-10,-10,1,3,-7,-7,-7,-7,3,1,-10,-10,-10,13],[10,-10,-10,1,3,-5,3,3,3,3,-5,3,1,-10,-10,10],[7,-10,1,3,-5,3,5,-5,-5,5,3,-5,3,1,-10,7],[3,1,3,-5,3,5,-5,3,3,-5,5,3,-5,3,1,3],[5,3,-5,3,5,-5,5,5,5,5,-5,5,3,-5,3,5],[3,-7,3,5,-5,5,5,10,10,5,5,-5,5,3,-7,3],[7,-7,3,-5,3,5,10,16,16,10,5,3,-5,3,-7,7],[7,-7,3,-5,3,5,10,16,16,10,5,3,-5,3,-7,7],[3,-7,3,5,-5,5,5,10,10,5,5,-5,5,3,-7,3],[5,3,-5,3,5,-5,5,5,5,5,-5,5,3,-5,3,5],[3,1,3,-5,3,5,-5,3,3,-5,5,3,-5,3,1,3],[7,-10,1,3,-5,3,5,-5,-5,5,3,-5,3,1,-10,7],[10,-10,-10,1,3,-5,3,3,3,3,-5,3,1,-10,-10,10],[13,-10,-10,-10,1,3,-7,-7,-7,-7,3,1,-10,-10,-10,13],[16,13,10,7,3,5,3,7,7,3,5,3,7,10,13,16]],"actions": []}'
      ),
      show: true
    };
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    }
  },
  computed: {
    tiled_point: function(_x, _y) {
      let x = this.res.tiled[_x];
      return x[_y];
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
