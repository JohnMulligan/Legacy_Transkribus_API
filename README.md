# Legacy_Transkribus_API and Website

# R-will-transkribus

## Transkribus Website Steps:

1. Create your own collection "New Collection"
2. Name the collection
3. Click on "Upload Document"
4. Click on "Quick Test Recognition"
5. Click "Handwritten"
7. Then choose a language: "English"
8. Click on the search bar (choose your collection)
9. Open your "File Explorer" on your PC
10. Choose image from there
11. Lastly, drag or drop your chosen image
12. Let image transcribe.

### Once Transription is finished:

13. Click on the finish product of the image thumbnail
14. Read and validate transcription


## Last Will and Testament of Isabell Midford
1706/ M.11

nthe name of (God Ilmen

I Isabell Midford of Longbenton in the County

of Horthumb: Spinster being weak & sickly of

body but of sound perfect and disposcing minde & memory

prayed be God Yet considering the Mortality of my week body

and for the sutisfying of my friends and Relations after my

death doe make and declare this my Laft will & Seftament

in manner and form following, firft & principally I committ

& Commend my soul unto the hands of Almighty God my maker

& Ceator and to Jesus Chrift my Redeemer and my body to

return to its premitive duft from whence it was taken to be

decently interred at the discretion of my Exca Revoaking and

Disanulling all other Wills and Testaments

As touching my temporall goods that God hath endowed me

withall I give & bequeath them in mant & form following

        **Imp**

I give & Bequeeath to my Nephen William Chambers som-

to my sifter ann Chambers the sum of Ten Pounds

        **Ste**

I give and bequeeath to my Nephew John Chambers son-

to my sifter Ann Chamber the sum of Ten Poundon

        **Iter**
I give & Bequeath to my Rease Mary Chambers daughter to my sifter dnm Chambers the sum of Tem Pounds

        **Ste**

I give and Bequeath to my Brother Thomas Chambers

all the the Reft of my goods moueable and unmovable

        **Laftly**

I conflitute and appoint my brother Thomas Chambers

to be my sole Execut of this my Laft Will & Teslament

he dischargeing my Debts and funerall expences

In witness whereof I have hereunto set to my hands

and seal the second day of March Ann Dom. 1700

        **099**

Wittness
Mt: Musgeare
Dabel Mitford
John Brown
Margaret Muggrave





## TRANSKRIBUS API


### Task 1: Return user information and session ID 

##LOGIN TO Transkribus

import requests

r = requests.post {'https://transkribus.eu/TrpServer/rest/auth/login', data ='user':'m-hutson@outlook.com', 'pw':}

print(r.text)

r.status_code


### Task 2: Upload image to API using session ID. This session ID was generated from the previous code.

##List of collections

sessionID = {'JSESSIONID': ''}

r = requests.get('https://transkribus.eu/TrpServer/rest/collecctions/list', params= sessionID)

print(r.text)


### Task 3: Document details from te collection

metadata = {
    
  'nd': {
        'title': 'default',
        "author": "default",
        "genre": "default",
        "writer": "default"
  },
  'pagelist':{
      'pages':[
          {
            'filename': 'R.jpg',
            'pageNr':1,
          }
      ]
  }
}

r = requests.post('https://transkribus', params= sessionID, json= metadata)

print(r.text)


### Task 4: Import files from google collab

from google.colab import files

files = {"img" : open('R.jpg','rb')}

r = requests.put('https://', files= files, params= sessionID)

print(r.text)


### Task 5 and 6: Get documents

r = requests.get('https://transkribus.eu', params= sessionID)

print(r.text)

r = requests.get('https://transkribus.eu', params= sessionID)

print(r.text)
