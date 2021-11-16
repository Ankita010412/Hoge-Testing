 'Systemutil.Run "C:\Users\tap6\Downloads\abc.vbs"
 'Dialog("nativeclass:=#32770","text:=Decrypt").WinEdit("nativeclass:=Edit").SetSecure "603a6b37ea7386eb941d265cd7784c5)

 SystemUtil.CloseProcessByName("chrome.exe")
 sURL = "https://anylogi-recruitment.web.app/"
 Systemutil.Run "chrome.exe", "https://anylogi-recruitment.web.app/",,,3
 Browser("name:=.*").Page("title:=.*").Sync
 'Browser("name:=.*").Navigate($URL)
 'Browser("name:=.*").Page("title:=.*").Sync
 'Wait(5)

 If Browser("name:=React App").Page("title:=React App").WebElement("innertext:=Hoge Bank").Exist(5) Then
     Print("Login Page Displayed")
 Else
     Print("Login Page is Not Displayed")
     exittest
 End If

 If Browser("name:=React App").Page("title:=React App").WebButton("name:=SIGNUP").Exist(5) Then
 Browser("React App").Page("React App").WebButton("name:=SIGNUP").Click
 End If

 sEmailID = "Avins"
 sPwd = "Hogebank1"
 If Browser("name:=React App").Page("title:=React App").WebEdit("type:=text").Exist(5) Then
    Browser("name:=React App").Page("title:=React App").WebEdit("type:=text").Click
    Browser("name:=React App").Page("title:=React App").WebEdit("type:=text").Set sEmailID

 if sEmailid= "" Then
      Print("User name cannot be blank")
     exittest
 ElseIf Instr(sEmailID," ")>1 Then
      Print("User name cannot contain whitespaces")
    exittest
  Else 
    Printf("User Name entered successfully")
  EndIf
 EndIf

 If Browser("name:=React App").Page("title:=React App").WebEdit("type:=password").Exist(5) Then
    Browser("name:=React App").Page("title:=React App").WebEdit("type:=password").Click
    Browser("name:=React App").Page("title:=React App").WebEdit("type:=password").Set sPwd

   pLen = Len(sPwd)
     If pLen<8 Then
       Print("Password cannot be less than 8 characters")
         exittest
     ElseIf pLen>32 Then
       Print("Password cannot be greater than 32 characters")
         exittest  
     Else
  
     Dim regEx

     Set regEx = CreateObject("vbscript.regexp")
  
     regEx.Pattern = "^.*(?=.*\d)(?=.*[A-Z]).*$"

     ValidatePassword = regEx.Test(sPwd)
     If ValidatePassword = FAlse Then
        Print("Password must contain upper case and Number")
        exittest
     EndIf
     Set regEx = Nothing
     End If
 End If

 If Browser("name:=React App").Page("title:=React App").WebButton("name:=SIGNUP").Exist(5) Then
 Browser("React App").Page("React App").WebButton("name:=SIGNUP").Click
 End If

 If Browser("name:=React App").Page("title:=React App").WebElement("innertext:=Hoge Bank").Exist(5) Then
    msgbox("Signed in Successfully")
    Else
    msgbox("Login Unsuccessful")
 End If

'To deposit money
  sDep = 1000
  sTransactionFee = 0
  Browser("name:=React App").Page("title:=React App").Link("name:=デポジット").Exist(5) Then
    Browser("name:=React App").Page("title:=React App").Link("name:=デポジット").Click

  If Browser("name:=React App").Page("title:=React App").WebEdit("name:=WebEdit").Exist Then
  Browser("name:=React App").Page("title:=React App").WebEdit("name:=WebEdit").set sDep
  EndIf

  if Browser("name:=React App").Page("title:=React App").WebElement("xpath:=//DIV[@id='root']/DIV[1]/DIV[1]/DIV[1]/SPAN[4]").Exist Then
  sTransactionFee = Browser("name:=React App").Page("title:=React App").WebElement("xpath:=//DIV[@id='root']/DIV[1]/DIV[1]/DIV[1]/SPAN[4]").GetRoProperty("innertext")

      If sTransactionFee = (sDep*0.3) Then
        Print("Transaction Fee is 30%)
      Else
        Print("Transaction Fee is not 30%)
      End If
  End If


  Browser("name:=React App").Page("title:=React App").WebButton("name:=Deposit").Click


    If Browser("name:=React App").Page("title:=React App").WebElement("innertext:=Transactions").Exist(3) Then
       Print("Deposit successful")
    Else
       Print("Deposit unsuccessful")
    End If
End If

'To withdraw money

sWithdraw = 1000
  sTransactionFee = 0
  Browser("name:=React App").Page("title:=React App").Link("name:=引き出す").Exist(5) Then
    Browser("name:=React App").Page("title:=React App").Link("name:=引き出す").Click

  If Browser("name:=React App").Page("title:=React App").WebEdit("name:=WebEdit").Exist Then
  Browser("name:=React App").Page("title:=React App").WebEdit("name:=WebEdit").set sWithdraw
  EndIf

  if Browser("name:=React App").Page("title:=React App").WebElement("xpath:=//DIV[@id='root']/DIV[1]/DIV[1]/DIV[1]/SPAN[4]").Exist Then
  sTransactionFee = Browser("name:=React App").Page("title:=React App").WebElement("xpath:=//DIV[@id='root']/DIV[1]/DIV[1]/DIV[1]/SPAN[4]").GetRoProperty("innertext")




      If sTransactionFee = (sWithdraw*0.3) Then
        Print("Transaction Fee is 30%)
      Else
        Print("Transaction Fee is not 30%)
      End If
  End If


  Browser("name:=React App").Page("title:=React App").WebButton("name:=Withdraw").Click


    If Browser("name:=React App").Page("title:=React App").WebElement("innertext:=Transactions").Exist(3) Then
       Print("Withdraw successful")
    Else
       Print("Withdraw unsuccessful")
    End If
End If

'Logout

 If Browser("name:=React App").Page("title:=React App").WebButton("name:=Logout").Exist Then

 Browser("name:=React App").Page("title:=React App").WebButton("name:=Logout").Click
End If
 SystemUtil.CloseProcessByName("chrome.exe")








