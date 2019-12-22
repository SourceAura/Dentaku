<template>
  <div class="about">
    <vs-row vs-justify="center" class="info-card">
      <vs-col type="flex" vs-justify="center" vs-align="center" vs-w="6">
        <vs-card >
          <div slot="header">
            <h3>
              Dentaku 0.0.1
            </h3>
          </div>
          <div>
            ...blah...maybe later lol.
          </div>
          <div slot="footer">
            <vs-row vs-justify="flex-end">
              <vs-button
                to="/"
                :color="colorx"
                color-text="rgb(50,50,50)"
                icon="home"
              ></vs-button>
              <vs-button :color="colorx" icon="code"></vs-button>
            </vs-row>
          </div>
        </vs-card>
      </vs-col>
    </vs-row>
  </div>
</template>

<script>
export default {
  data() {
    return{
      colorx: "rgba(16,10,28, 0.8)"
    }
  }
}
</script>

<style lang="css" scoped>
@import url("https://fonts.googleapis.com/css?family=Shadows+Into+Light&display=swap");

.about {
  color: black;
  font-family: "Shadows Into Light", cursive;
}

.info-card {
  margin-top: 70px;
}
</style>
