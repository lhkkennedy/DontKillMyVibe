<template>
    <v-card height="330">
        <v-list>
            <v-list-item v-for="(track, index) in playlist" :key="track.title" v-show="track.display">
                <v-list-item-content>
                    <v-list-item-title>
                        {{ this.trackNumbers(index) }} {{  track.artist }} - {{ track.title }}
                    </v-list-item-title>
                </v-list-item-content>
                <v-spacer>
                </v-spacer>
                {{ this.trackMinutes(track.howl.duration) }}
            </v-list-item>
        </v-list>
    </v-card>
</template>

<script>
export default {
    props: {
        playlist: Array
    },
    methods: {
        trackNumbers(value) {
            let number = value + 1
            if (number < 10) {
                return "0" + number + "."
            }
            return number + "."
        },

        trackMinutes(value) {
            if (!value || typeof value !== "number") return "00:00"
            let min = parseInt(value / 60), sec = parseInt(value % 60)
            min = min < 10 ? "0" + min : min
            sec = sec < 10 ? "0" + sec : sec
            value = min + ":" + sec
            return value
        },
    }
}
</script>
