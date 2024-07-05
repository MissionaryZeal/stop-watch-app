<template>
    <div class="stopwatch">
        <h1>{{ formattedTime }}</h1>
        <div class="button-group">
            <button @click="start">{{ running ? 'Running' : 'Start' }}</button>
            <button @click="stop">Stop</button>
            <button @click="reset">Reset</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            time: 0,
            running: false,
            timer: null,
        };
    },
    computed: {
        formattedTime() {
            return this.formatTime(this.time);
        },
    },
    methods: {
        start() {
            if (!this.running) {
                this.running = true;
                this.timer = setInterval(() => {
                    this.time += 10;
                }, 10);
            }
        },
        stop() {
            this.running = false;
            clearInterval(this.timer);
            this.timer = null;
        },
        reset() {
            this.stop();
            this.time = 0;
        },
        formatTime(ms) {
            let milliseconds = parseInt((ms % 1000) / 10);
            let seconds = Math.floor((ms / 1000) % 60);
            let minutes = Math.floor((ms / (1000 * 60)) % 60);
            let hours = Math.floor((ms / (1000 * 60 * 60)) % 24);

            return (
                (hours < 10 ? "0" + hours : hours) +
                ":" +
                (minutes < 10 ? "0" + minutes : minutes) +
                ":" +
                (seconds < 10 ? "0" + seconds : seconds) +
                "." +
                (milliseconds < 10 ? "0" + milliseconds : milliseconds)
            );
        },
    },
};
</script>

<style scoped>
.stopwatch {
    display: flex;
    flex-direction: column;
    align-items: center;
    font-family: Arial, sans-serif;
}

.stopwatch h1 {
    padding: 6px 12px;
    border-radius: 4px;
    box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
}

.button-group {
    display: flex;
    justify-content: space-between;
}

button {
    margin: 5px 8px;
    border: none;
    color: white;
}

button:nth-child(1) {
    background-color: blue;
}

button:nth-child(2) {
    background-color: red;
}

button:nth-child(3) {
    background-color: black;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    margin: 5px 0;
}
</style>