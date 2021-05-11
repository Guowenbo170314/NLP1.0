# NLP1.0
调用百度API，进行中文姓名、企业名称识别
import time
from aip import AipNlp
APP_ID='240943'
API_KEY = 'HmneZkleVM6LC57BCzQGW5'
SECRET_KEY = 'MHOC2Mh5rPxjk7HEtlk4IzVnhlsI9h'
client = AipNlp(APP_ID, API_KEY, SECRET_KEY)
def get_chinese_name(text):
	text = str(text.encode('gbk', 'ignore'), encoding='gbk')
	time.sleep(1)
	for i in client.lexer(text)['items']:
		if i['ne'] == 'PER' or i['ne'] == 'ORG':
			print(i['item'])		
text='员工张三，在中国银行工作'
print(get_chinese_name(text))
