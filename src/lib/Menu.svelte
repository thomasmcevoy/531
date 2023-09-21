<script>
  export let exercises, settings;
</script>

<!-- <div id="settings-button">⚙</div> -->
<!-- ▾ -->

<div id="menu-container">
  <div id="menu-button" @click="$emit('toggle-menu')">≡</div>
  <div id="menu" v-if="isOpen">
    <!-- <div class="menu-item">
      <input type="email" v-model="email" name="email" placeholder="EMAIL">
      <input type="password" v-model="password" name="password" placeholder="PASSWORD">
      <button @click="signIn">SIGN IN</button>
      <button @click="register">REGISTER</button>
    </div> -->
    <div class="menu-item">
      <div>Smallest increment</div>
      <input
        type="radio"
        name="increment"
        id="2.5"
        value="2.5"
        v-bind:checked="this.increment === 2.5"
        @click="$emit('set-increment', 2.5)"
      />
      <label for="2.5">2.5 lbs</label>
      <input
        type="radio"
        name="increment"
        id="5"
        value="5"
        v-bind:checked="this.increment === 5"
        @click="$emit('set-increment', 5)"
      />
      <label for="5">5 lbs</label>
    </div>
    <div class="menu-item">
      <div>Exercises</div>
      <input
        type="checkbox"
        name="press"
        v-model="this.exercises[0].isVisible"
      />
    </div>
  </div>
</div>

<style>
  #settings-button {
    position: absolute;
    top: 0.5em;
    right: 0.667em;
    font-size: 1.5em;
    font-weight: 100;
    color: #aaa;
  }
  #settings-button:hover {
    cursor: pointer;
  }
</style>
