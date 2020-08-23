<template>
  <div id="app">
    <section class="hero is-light is-fullheight">
        <div class="hero-body">
            <div class="container">
                <Header/>
                <AddParticipant v-on:add-Participant="addParticipant" />
            </div>
        </div>
    </section>
     
  </div>
</template>

<script>
import AddParticipant from '../components/AddParticipant';
import axios from 'axios';


export default {
  name: 'App',
  components: {
    AddParticipant
  },
  data() {
    return {
      participants: []
    }
  },
  methods: {
    addParticipant(newParticipant) {
      var { name, manager, type_of_participant, foundation_date} = newParticipant;
      var data = {name, manager, type_of_participant,foundation_date};

      var config = {
        method: 'post',
        url: 'http://localhost:8000/participant/',
        headers: { 
          'Content-Type': 'application/json'
        },
        data : data
      };

      axios(config)
      .then(data => {
          const config = {
            method: 'get',
            url: 'http://localhost:8000/participant/'
          };
          console.log(data);
          axios(config)
            .then(res => this.participants = res.data)
            .catch(error => console.log(error));
      })
      .catch(function (error) {
        console.log(error);
      });
    }
  },
  created() {
    const config = {
      method: 'get',
      url: 'http://localhost:8000/participant/'
    };
    axios(config)
      .then(res => this.participants = res.data)
      .catch(error => console.log(error));
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}


</style>
