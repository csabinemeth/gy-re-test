<template>
  <div class="background">
    <div class="row">
      <button
        type="button"
        class="btn btn-success"
        id="generatorBtn"
        @click="randomNumberGerator()"
      >
        Random szám
      </button>
      <input
        type="text"
        class="form-control"
        id="randomResult"
        v-model="this.randomNum"
        placeholder="Random number"
        disabled
      />

      <input type="date" v-model="this.date"/>
    </div>

    <div class="row">
      <input
        type="email"
        class="form-control"
        id="email1"
        v-model="this.email1"
        placeholder="name@example.com"
      />
      <input
        type="email"
        class="form-control"
        id="email2"
        v-model="this.email2"
        placeholder="name@example.com"
      />
      <p id="alertMessage">A két e-mailcím nem azonos!</p>
      <button
        type="button"
        class="btn btn-primary"
        id="checkBtn"
        @click="checkEmails()"
      >
        Check
      </button>
    </div>
    <div class="row">
      <input type="email" class="form-control" id="addEmail" v-model="this.addedEmail" placeholder="name@example.com">
      <button class="btn btn-success" id="addBtn" @click="addEmail()">Add</button>
      <button class="btn btn-primary" id="writeBtn" @click="writeEmails()">Write</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },

  data() {
    return {
      randomNum: 0,

      email1: undefined,
      email2: undefined,

      date: undefined,

      emails: [],
      addedEmail: undefined,
    };
  },

  methods: {
    randomNumberGerator() {
      this.randomNum = Math.floor(Math.random() * 6 + 1);

      if (this.randomNum == 6) {
        console.log("hatosd dobtál");
      }

      console.log(this.randomNum);
      console.log(this.date);
    },

    checkEmails() {
      if (this.email1 != this.email2) {
        document.getElementById("alertMessage").style.display = "block";
      } else {
        document.getElementById("alertMessage").style.display = "none";
      }
    },

    addEmail(){
      this.emails.push(this.addedEmail);
    },

    writeEmails(){
      for(let i = 0; i < this.emails.length; i++){
        console.log(this.emails[i]);
      }
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.background {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

#alertMessage {
  display: none;
  color: red;
}

#generatorBtn {
  margin-top: 20px;
  max-width: 150px;
  margin-bottom: 20px;
}

#randomResult {
  max-width: 150px;
}

.row {
  display: flex;
  flex-direction: column;
  position: relative;
  margin-left: 100px;
}

#email1 {
  margin-bottom: 20px;
  max-width: 300px;
}

#email2 {
  max-width: 300px;
  margin-bottom: 20px;
}

#checkBtn {
  max-width: 150px;
}

#addEmail{
  margin-bottom: 10px;
}

#addBtn{
  margin-bottom: 10px;
}
</style>
