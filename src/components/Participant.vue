<template>
    <tr>
        <th>{{participant.sid}}</th>
        <td>{{participant.name}}</td>
        <td>{{participant.manager}}</td>
        <td>{{participant.type_of_participant}}</td>
        <td>{{participant.foundation_date}}</td>
        <td>
            <button class="button is-small" v-on:click="moveParticipantUp(participant)" v-if="participant.sid != 1">
                <span class="icon fa fa-arrow-up" name="up">
                </span>
            </button>
            <button class="button is-small" v-on:click="moveParticipantDown(participant)" v-if="participant.sid != participants.length">
                <span class="icon fa fa-arrow-down">
                </span>
            </button>
        </td>
    </tr>
</template>

<script>
export default {
    name: "Participant",
    props: ["participant", "participants"],
    methods: {
        moveParticipantUp(participant) {
            let participantSid = participant.sid - 1;
            let tempParticipant = this.participants[participantSid];
            tempParticipant.sid = participantSid;
            this.participants[participantSid - 1].sid = participant.sid + 1;
            this.participants.splice(participantSid, 1);
            this.participants.splice(participantSid - 1, 0, tempParticipant);
            this.participants.join();
        },
        moveParticipantDown(participant) {
            let participantSid = participant.sid - 1;
            let tempParticipant = this.participants[participantSid];
            tempParticipant.sid = participant.sid + 1;
            this.participants[participantSid + 1].sid = participant.sid - 1;
            this.participants.splice(participantSid, 1);
            this.participants.splice(participantSid + 1, 0, tempParticipant);
            this.participants.join();
        }
    }
    
}
</script>
