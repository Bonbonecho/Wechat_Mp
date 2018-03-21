import itchat
import requests

KEY = '8edce3ce905a4c1dbb965e6b35c3834d'


@itchat.msg_register(itchat.content.TEXT)
def ai_response(msg):
    fromUser = msg.fromUserName
    if fromUser in targetUsers:
        return get_response(msg.text)


def searchFriend():
    friends_list = itchat.search_friends(remarkName='女朋友')
    for friend in friends_list:
        targetUsers.append(friend.UserName)


def get_response(text):
    apiUrl = 'http://www.tuling123.com/openapi/api'
    data = {
        'key': KEY,
        'info': text,
        'userid': 'cpak00',
    }
    try:
        r = requests.post(apiUrl, data=data).json()
        return r.get('text')
    except:
        return


if __name__ == '__main__':
    global targetUsers
    targetUsers = []
    itchat.auto_login(hotReload=True, loginCallback=searchFriend)
    itchat.run()
