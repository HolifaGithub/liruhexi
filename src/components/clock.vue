<template>
  <div id="clock">
    <p class="date">{{ date }}</p>
    <p class="time">{{ time }}</p>
    <p class="text">Display Huanglifeng、 Zhanghe、 Huangshanru and Wangxi</p>
</div>
</template>

<script>

import { ref } from 'vue'

export default {
    setup(){
        const date = ref("");
        const time = ref("");
        var week = ['SUN', 'MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT'];
        var timerID = setInterval(updateTime, 1000);
        updateTime();
        function updateTime() {
            var cd = new Date();
            time.value = zeroPadding(cd.getHours(), 2) + ':' + zeroPadding(cd.getMinutes(), 2) + ':' + zeroPadding(cd.getSeconds(), 2);
            date.value = zeroPadding(cd.getFullYear(), 4) + '-' + zeroPadding(cd.getMonth()+1, 2) + '-' + zeroPadding(cd.getDate(), 2) + ' ' + week[cd.getDay()];
        };

        function zeroPadding(num, digit) {
            var zero = '';
            for(var i = 0; i < digit; i++) {
                zero += '0';
            }
            return (zero + num).slice(-digit);
        }
        return {date,time}
    }
}
</script>

<style scpoed>
p {
  margin: 0;
  padding: 0;
}

#clock {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  font-family: 'Share Tech Mono', monospace;
  color: #ffffff;
  text-align: center;
background-image: linear-gradient(to right, pink 0%, skyblue 100%);
  color: #daf6ff;
  text-shadow: 0 0 20px #0aafe6, 0 0 20px rgba(10, 175, 230, 0);
}
#clock .time {
  letter-spacing: 0.05em;
  font-size: 3rem;
  padding: 5px 0;
}
#clock .date {
  letter-spacing: 0.1em;
  font-size: 1.2rem;
}
#clock .text {
  letter-spacing: 0.1em;
  font-size: 1rem;
  padding: 0.3rem 0 0;
}
</style>