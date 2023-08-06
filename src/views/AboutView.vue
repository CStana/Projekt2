<template>
  <div>
    <v-card class="mx-auto" dark style="background-color:#181818">
      <v-card-title style="padding-top:50px;">
        <span class="text-h3 font-weight-light white--text">Vaš komentar</span>
      </v-card-title>

      <v-card-text class="text-h6 white--text">
        Ostavite svoj komentar. Nama je to vrlo važno jer žeilmo
        znati ima li problema na stranici. Ukoliko naiđete na neki problema
        ne ustručavajte se napisati svoj komentar. Kako bi mi uvidjeli greške
        i ispravili. Unaprijed se zahvaljujemo!
      </v-card-text>
      <div class="text-input-container">
        <v-textarea
          outlined
          label="KOMENTAR"
          placeholder="Ostavite svoj komentar..."
          class="custom-textarea"
          rows="5"
        ></v-textarea>
        <v-btn
          :loading="loading3"
          :disabled="loading3"
          color="#921616"
          class="ma-2 white--text"
          @click="loader = 'loading3'"
        >
          Upload
          <v-icon right dark>mdi-movie</v-icon>
        </v-btn>
      </div>
    </v-card>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.custom-textarea {
  color: white;
  background-color: transparent;
  border-color: white;
  border-radius: 5px;
  padding: 10px;
}

.custom-textarea::placeholder {
  color: white;
}

.text-input-container {
  display: flex;
  align-items: center;
}

.v-textarea--solo {
  margin-right: 10px;
}

.v-btn.indigo {
  background-color: #000000;
}

.v-btn.indigo .v-icon {
  font-size: 20px;
  margin-left: 6px;
}
</style>
