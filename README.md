# Hxc-project
我的第一个 GitHub 仓库

【运维权限信息】
公司虚拟平台
https://10.1.1.253:8443
虚拟机QAX-2016
admin
Youpai@2807
个人虚拟机：192.168.8.10
登录权限：
hxc/root    ubuntu123

【AI学习】
本地模型服务器：10.1.1.181
本地dify服务器：10.1.1.174
登录权限：root/Youpai@2807
Dify-174
huangxc@cdyoupai.com
Hxc123.abc
平台链接
个人dify平台：http://192.168.8.10/    admin/dify@12345
公司dify平台：http://10.1.1.174/     admin/Youpai@2807
个人虚拟机AI网关：http://192.168.8.10:8080/   admin/Youpai@2807
公司本地AI网关：http://10.1.1.181:8080/      admin/Youpai@2807
山石Woi部署中心：http://10.1.1.177:8443/     woi/Youpai@2807
山石Woi用户登录：https://10.1.1.177          huangxc/Youpai@2807

【公网模型】
智谱大模型https://bigmodel.cn/console/overview
173手机号
API-KEY  f173ec610234455d845a7420824ceb21.I1J3LlGficBnMXLZ
【测试方法】
curl -X POST "https://open.bigmodel.cn/api/paas/v4/chat/completions" -H "Content-Type: application/json" -H "Authorization:f173ec610234455d845a7420824ceb21.I1J3LlGficBnMXLZ" -d '{
    "model": "glm-5.3",
    "messages": [
        {
            "role": "system",
            "content": "你是一个有用的AI助手。"
        },
        {
            "role": "user",
            "content": "你好，请介绍一下自己。"
        }
    ],
    "temperature": 1.0,
    "stream": true
}'

【脱敏代码】
原代码
import re
def main(text: str) -> dict:
    # 1. 基础清洗：将多行/多空格合并为单空格
    cleaned_text = re.sub(r'\s+', ' ', text.strip())
    
    # 2. 敏感信息脱敏（防止泄露手机号/身份证给外部LLM）
    # 手机号脱敏
    cleaned_text = re.sub(r'(\d{3})\d{4}(\d{4})', r'\1****\2', cleaned_text)
    # 身份证号脱敏
    cleaned_text = re.sub(r'(\d{6})\d{8}(\d{4})', r'\1********\2', cleaned_text)
    
    return {
        "sanitized_text": cleaned_text
    }
AI建议代码
import re
def main(text: str) -> dict:
    cleaned = re.sub(r'(\d{3})\d{4}(\d{4})', r'\1****\2', text)
    cleaned = re.sub(r'(\d{6})\d{8}(\d{4})', r'\1********\2', cleaned)
    return {"sanitized_text": cleaned.strip()}   # 保留 \n 与 Markdown
