<template>
<div class="chat-main">
    <TransitionGroup name="list">
        <div class="chat-main-item" v-for="(msg, idx) in msgs" :key="idx">
            <div class="chat-main-item-content" :class="{
                send: msg.sendId == sender,
                get: msg.sendId != sender
            }">
                <span>{{msg.time}}</span>
                <div>
                    <!-- <img src="" alt=""> -->
                    <p>{{msg.body}}</p>
                </div>
            </div>
        </div>
    </TransitionGroup>
</div>
</template>
<script>
export default {
    props: ['msgs', 'sender'],
}
</script>
<style>
    
</style>