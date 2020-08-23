<template>
    <div>
        <div class="table-container">
            <table class="table is-bordered is-fullwidth">
                <thead>
                    <th><abbr title="Id">Turn</abbr></th>
                    <th><abbr title="Name"></abbr>Name</th>
                    <th><abbr title="Manager"></abbr>Manager</th>
                    <th><abbr title="type_of_participant"></abbr>Type Of Participant</th>
                    <th><abbr title="foundation_date"></abbr>Foundation Date</th>
                    <th><abbr title="move"></abbr>Move</th>
                </thead>
                <tbody v-bind:key="participant.id" v-for="participant in participants">
                    <Participant v-bind:participant="participant" v-bind:participants="participants"/>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import Participant from './Participant.vue';

export default {
    name: "Participants",
    components: {
        Participant
    },
    props: ["participants"]
}
</script>

<style scoped>

</style>