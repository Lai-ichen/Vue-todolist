<template>
    <div class="chatbot">
        <div class="chatbot-messages">
            <div v-for="message in messages" :key="message.id" class="message">
                <div v-if="message.isBot" class="bot-message">
                    {{ message.text }}
                </div>
                <div v-else class="user-message">
                    {{ message.text }}
                </div>
            </div>
        </div>
        <div class="chatbot-input">
            <input v-model="newMessage" @keyup.enter="sendMessage" placeholder="輸入訊息..." />
            <button @click="sendMessage">送出</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            messages: [],
            newMessage: ""
        };
    },
    methods: {
        sendMessage() {
            if (this.newMessage.trim() !== "") {
                this.messages.push({
                    id: Date.now(),
                    text: this.newMessage,
                    isBot: false
                });
                this.newMessage = "";
                // 在這裡處理回覆訊息的邏輯，例如呼叫 API 或觸發其他事件
            }
        }
    }
};
</script>

<style scoped>
.chatbot {
    display: flex;
    flex-direction: column;
    height: 400px;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 10px;
}

.chatbot-messages {
    flex: 1;
    overflow-y: auto;
}

.message {
    margin-bottom: 10px;
}

.bot-message {
    background-color: #f0f0f0;
    padding: 5px;
    border-radius: 4px;
}

.user-message {
    background-color: #e0e0e0;
    padding: 5px;
    border-radius: 4px;
}

.chatbot-input {
    display: flex;
    align-items: center;
    margin-top: 10px;
}

input {
    flex: 1;
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-right: 10px;
}

button {
    padding: 5px 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 10px;
    cursor: pointer;
}
</style>