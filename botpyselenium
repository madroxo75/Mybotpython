from selenium import webdriver
import time
import os
from selenium.webdriver.chrome.options import Options 
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import requests
import openai


dir_path = os.getcwd() 
chrome_options2 = Options()
chrome_options2.add_argument(r"user-data-dir="+dir_path +"profile/save") 
driver = webdriver.Chrome(chrome_options2)
driver.get('https://web.whatsapp.com')
agent = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.36'}
time.sleep(10)


api = requests.get("http://editacodigo.com.br/index/api-whatsapp/YqNSHpaYJTCkeJ9OlEzFa2p6ujKZQPDn", headers = agent)
time.sleep(1)
api = api.text
api = api.split(".n.")
bolinha_notificacao = api[3].strip()
contato_cliente = api[4].strip()
caixa_msg = api[5].strip
msg_cliente = api[6].strip()
############ api do edita codigo
def bot():
     
    try:
        ############## pegar a mensagem e dar o clique nela
        bolinha = driver.find_element(By.CLASS_NAME,bolinha_notificacao)
        bolinha = driver.find_elements(By.CLASS_NAME,bolinha_notificacao)
        clica_bolinha = bolinha[-1]
        acao_bolinha = webdriver.common.action_chains.ActionChains(driver)
        acao_bolinha.move_to_element_with_offset(clica_bolinha,0,-20)
        acao_bolinha.click()
        acao_bolinha.perform()
        acao_bolinha.click()
        acao_bolinha.perform()

        ############### ler nova mensagem
        todas_as_msg = driver.find_elements(By.CLASS_NAME,msg_cliente)
        todas_as_msg_texto = [e.text for e in todas_as_msg]
        msg = todas_as_msg_texto[-1]
        print(msg)
    




        #################processar na api
        openai.api_key = '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'
        response = openai.Completion.create(
        model = "text-davinci-003",
        prompt =msg,
        temperature = 0.7,
        max_tokens = 256,
        top_p = 1,
        frequency_penalty = 0,
        presence_penalty = 0    
        )
        resposta = response['choices'][0]['text']
        time.sleep(10)



        ####################responder mensagem e fechar o contato
        campo_de_texto = driver.find_element(By.XPATH,caixa_msg)
        campo_de_texto.click()
        time.sleep(3)
        campo_de_texto.send_keys(resposta,Keys.ENTER)
        webdriver.ActionChains(resposta).send_keys(keys.ENTER).perform()
        time.sleep(20)

         
    except:
        print("Tô só cuidando da sua vida, seu humano preguiçoso")
        time.sleep(30)
while True:
    bot()


       







    
