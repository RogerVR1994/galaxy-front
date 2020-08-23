<template>
    <div class="field has-addons has-addons-centered">
        <form @submit="addParticipant">

            <div class="field">
                <p class="control has-icons-left has-icons-right">
                    <input class="input" v-model="name" type="text" name="name" placeholder="Name"> 
                    <span class="icon is-small is-left">
                    <i class="fa fa-user"></i>
                    </span>
                </p>
            </div>

            <div class="field">
                <p class="control has-icons-left has-icons-right">
                    <input class="input" v-model="manager" type="text" name="manager" placeholder="Manager Email">
                    <span class="icon is-small is-left">
                    <i class="fas fa-envelope"></i>
                    </span>
                </p>
            </div>
           <div class="field-body">
               <div class="select is-fullwidth">
                    <select name="type_of_participant" v-model="type_of_participant">
                        <option>Band</option>
                        <option>Carriage</option>
                    </select>
                </div>
                
                <datepicker class="input" v-model="date" lang="en" type="date" format="yyyy-MM-dd"></datepicker>

               <p class="control">
                   <input type="submit" value="Submit" class="button is-primary">
               </p>
           </div>
            
            
            
        </form>
    </div>
    
</template>

<script>
import Datepicker from 'vuejs-datepicker';

export default {
    name: "AddParticipant",
    components: {
        Datepicker
    },
    props: [
        "state"
    ],
    data() {
        return {
            name: '',
            manager: '',
            type_of_participant: '',
            foundation_date: '',
            date: new Date()
        }
    },
    methods: {
        addParticipant(e) {
            e.preventDefault();
            const newParticipant = {
                name: this.name,
                manager: this.manager,
                type_of_participant: this.type_of_participant,
                foundation_date: this.date.toISOString().slice(0,10)
            }
            console.log(this.date.toISOString().slice(0,10));

            this.$emit('add-Participant', newParticipant);
            this.name = "";
            this.manager = "";
        }
    }
}
</script>

<style>
</style>