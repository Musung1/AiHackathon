<template>
	<div style="height:192px; background-color: #FEF8F1;" ></div>

	<div id="app">
    <div id="conversation-list">
      <!-- 대화방 리스트 -->
      <div class="conversation" v-for="(conversation, index) in conversations" :key="index" :class="{ 'selected-conversation': index === selectedConversationIndex }" @click="selectConversation(index)">
				<div class="conversation-info">
          <div class="conversation-title">{{ conversation.name }}</div>
          <div class="conversation-date">{{ conversation.createdAt }}</div>
        </div>
      </div>
    </div>
    <div id="conversation-content">
      <!-- 선택된 대화 내용 -->
      <div v-if="selectedConversation !== null">
        <div class="conversationRoom-title">{{ selectedConversation.name }}</div>
        <div class="messages">
					<div class="message" v-for="(message, index) in selectedConversation.messages" :key="index">
            <div v-if="message.sender === 'me'" class="right-message">
              <!-- 나의 메시지 -->
              <div class="my-message-bubble">
                {{ message.text }}
              </div>
            </div>
            <div v-else class="left-message">
              <!-- 상대방의 메시지 -->
              <img src="../../assets/monster.png" alt="상대방 아이콘" class="user-icon" />
              <div class="your-message-bubble">
                {{ message.text }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
	
	<div style="height:192px; background-color: #FEF8F1;" ></div>

</template>

<script>
// export default {
	
// }

export default {
  data() {
    return {
      conversations: [
		/////

				{ name: '편식하지 말자', createdAt: '2023년 8월 28일 (월) 09:55', 
					messages: [
											{ text: '피자만 먹던 한석이가 다양한 음식을 시도해 보게 된 계기가 뭐라고 생각하니?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '음, 다양한 맛을 맛보게 해줘서 그랬다기 보다는 내 생각엔 건강이 안좋아져서 그랬던 것 같아. 몸이 아프니까 많은 것을 느꼈던게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '좋은 의견이네! 네 말을 들어보니까, 그게 더 맞는 것 같아. 나도 편식을 하다가 비타민이 부족해서 아팠던 적이 있었는데 너무 힘들었거든.', sender: 'me' }
										] 
				},
				{ name: '지구를 지키자', createdAt: '2023년 8월 27일 (일) 14:13', 
					messages: [
											{ text: '피자만 먹던 한석이가 다양한 음식을 시도해 보게 된 계기가 뭐라고 생각하니?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }
										] 
				},


				/////
        { name: '쓰레기를 버리지 말자', createdAt: '2023년 8월 26일 (토) 12:02', 
					messages: [
											{ text: '피자만 먹던 한석이가 다양한 음식을 시도해 보게 된 계기가 뭐라고 생각하니?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }
										] 
				},
        { name: '음식을 남기지 말자', createdAt: '2023년 8월 25일 (금) 08:53', 
					messages: [
											{ text: '피자만 먹던 한석이가 다양한 음식을 시도해 보게 된 계기가 뭐라고 생각하니?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }
										] 
				},
        { name: '횡단보도에서 뛰지 말자', createdAt: '2023년 8월 24일 (목) 18:32', 
					messages: [
											{ text: '피자만 먹던 한석이가 다양한 음식을 시도해 보게 된 계기가 뭐라고 생각하니?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }
										] 
				},
        { name: '인사를 잘하자', createdAt: '2023년 8월 23일 (수) 16:25', 
					messages: [
											{ text: '피자만 먹던 한석이가 다양한 음식을 시도해 보게 된 계기가 뭐라고 생각하니?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }
										] 
				},
        { name: '아파트에서 뛰지 말자', createdAt: '2023년 8월 22일 (화) 15:21', 
					messages: [
											{ text: '피자만 먹던 한석이가 다양한 음식을 시도해 보게 된 계기가 뭐라고 생각하니?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }
										] 
				},
        { name: '이웃한테 존댓말 하자', createdAt: '2023년 8월 21일 (월) 06:51', 
					messages: [
											{ text: '피자만 먹던 한석이가 다양한 음식을 시도해 보게 된 계기가 뭐라고 생각하니?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }
										] 
				},
        { name: '친구랑 싸우지 말자', createdAt: '2023년 8월 20일 (일) 11:38', 
					messages: [
											{ text: '피자만 먹던 한석이가 다양한 음식을 시도해 보게 된 계기가 뭐라고 생각하니?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }, 
											{ text: '나도 그렇게 생각해. 새로운 친구들이 다양한 맛을 맛보게 해줬던게 크지 않았을까?', sender: 'other' },
											{ text: '공원에서 한석이가 새로운 친구들을 만났는데,  걔네가 다양한 음식을 먹는 것을 좋아하고 다양한 맛을 즐기는 것을 보여줘서 시도 해본게 아닐까?', sender: 'me' }
										] 
				}
        // 추가 대화방을 여기에 추가할 수 있습니다.
      ],
      selectedConversation: null,
			selectedConversationIndex: 0
    };
  },
	created() {
    // 페이지가 로드될 때 첫 번째 대화방을 선택하도록 초기화합니다.
    if (this.conversations.length > 0) {
      this.selectedConversation = this.conversations[0];
    }
  },
  methods: {
    selectConversation(index) {
      this.selectedConversation = this.conversations[index];
			this.selectedConversationIndex = index;
    },
  },
};

</script>

<style scoped>

#app {
  display: flex;
	background-color: #FEF8F1;
}

#conversation-list {
  width: 372px;
	max-height: 816px;
  overflow-y: auto;
	margin-left: 155px;
}

#conversation-content {
  width: 852px;
  overflow-y: auto;
	margin-left: 108px;
}

.selected-conversation {
	background-color: #7669DF !important;
}
.selected-conversation .conversation-title {
	color: white;
}
.selected-conversation .conversation-date {
	color: white;
}

.conversation {
  padding: 10px;
	width: 330px;
	height: 120px;

	border-radius: 999px;
	margin-bottom: 24px;
  background-color: #FFFFFF;
  cursor: pointer;
	display: flex;
  align-items: center;
}

.conversation-info {
	margin: 32px 40px;
}

.conversation-title {
  color: var(--text-light-500, #373737);
	font-family: Pretendard;
	font-size: 24px;
	font-style: normal;
	font-weight: 700;
	line-height: normal;
	text-align: left;
	margin-bottom: 8px;
}

.conversation-date {
  color: var(--text-light-300, rgba(55, 55, 55, 0.50));
	font-family: Pretendard;
	font-size: 16px;
	font-style: normal;
	font-weight: 500;
	line-height: normal;
	text-align: left;
}

.messages {
	max-height: 688px;
  overflow-y: auto;
}

 .message {
	font-family: Pretendard;
	font-size: 23.06px;
	font-style: normal;
	font-weight: 700;
	line-height: normal;
} 
.conversationRoom-title {
	width: 807px;
	height: 72px;
	line-height : 72px;
	margin-bottom: 56px;
	color: var(--text-dark-500, #FFF);
	text-align: center;
	font-family: Pretendard;
	font-size: 32px;
	font-style: normal;
	font-weight: 700;
	border-radius: 999px;
	background: var(--main-sub-500, #FFB547);
}

.left-message {
  display: flex;
	align-items: center;
}

/*
.right-message {
  text-align: right; 
	margin-left: 250px;
} */

.my-message-bubble {
	text-align: right; /* 나의 말한 내용 오른쪽 정렬 */
	margin-left: 250px;
	width: 572px;
	height: 128px;
	padding: 22px 46px;
	border-radius: 68px;
	background-color: white;
}

.your-message-bubble {
	text-align: left; /* 상대방이 말한 내용 왼쪽 정렬 */
	width: 572px;
	height: 100px;
	margin: 22px 46px;
	padding: 22px 46px;
	border-radius: 68px 68px 68px 0px;
	background-color: #646464;
	color: white;
}

.user-icon {
  width: 68px; /* 아이콘의 너비 조절 */
  height: 78px; /* 아이콘의 높이 조절 */
  margin-right: 5px; /* 아이콘과 메시지 사이의 간격 설정 */
}

</style>