# week2_vba_challenge
updated code
please check column O,P,Q for greatest decrease, increase, and volume
since in the last grading it looks like you didnt swipe right to see results. thank you.

Sub module2()

'declare variables  Dim ticker As String
  Dim ticker As String
  Dim open_stock As Double
  Dim closing_stock As Double
  Dim yearly_ch As Double
  Dim percent_ch As Double
  Dim Summary_Table_Row As Integer
  Dim volume As LongLong
  Dim startDate As String
  Dim endDate As String
  
  
  
  
  Dim ws As Worksheet
  For Each ws In ActiveWorkbook.Worksheets
  
  Summary_Table_Row = 2
  volume = 0
 
 startDate = ws.Range("b2").Value
endDate = ws.Range("b" & Range("b:b").Rows.Count).End(xlUp).Value

open_stock = ws.Cells(2, 3).Value
  closing_stock = ws.Cells(2, 6).Value
  
  For i = 2 To 753001
  
  
  
    If ws.Cells(i + 1, 1).Value <> ws.Cells(i, 1).Value Then

 
     ticker = ws.Cells(i, 1).Value
      
     volume = volume + ws.Cells(i, 7).Value
      
     'open_stock = open_stock + Cells(i, 3).Value
     
     'closing_stock = closing_stock + Cells(i, 6).Value
     
     closing_stock = ws.Cells(i, 6).Value
     
     yearly_ch = closing_stock - open_stock
     
     percent_ch = yearly_ch / open_stock * 100
     
     open_stock = ws.Cells(i + 1, 3).Value
     
       
ws.Range("L" & Summary_Table_Row).Value = volume
ws.Range("j" & Summary_Table_Row).Value = yearly_ch
ws.Range("k" & Summary_Table_Row).Value = percent_ch
ws.Range("i" & Summary_Table_Row).Value = ticker
   
      

ws.Range("i1").Value = "ticker"
ws.Range("j1").Value = "yearly change"
ws.Range("k1").Value = "percent chang"
ws.Range("L1").Value = "total volume"
        
    

   
      Summary_Table_Row = Summary_Table_Row + 1
     

    Else

     volume = volume + ws.Cells(i, 7).Value
     
         
    If ws.Cells(i, 10).Value > 0 Then
    ws.Cells(i, 10).Interior.ColorIndex = 4
    ElseIf ws.Cells(i, 10).Value < 0 Then
    ws.Cells(i, 10).Interior.ColorIndex = 3
    
    Else: ws.Cells(i, 10).Interior.ColorIndex = 0
    
    End If
    

    End If

    
    
    
  Next i
  
 ws.Cells(1, 16).Value = "ticker"
 ws.Cells(1, 17).Value = "value"
 ws.Cells(2, 15).Value = "greatest % increase"
 ws.Cells(3, 15).Value = "greatest % decrease"
 ws.Cells(4, 15).Value = "greatest total volume"
 

'part two


    Dim stockWithGreatestVolume As String
    Dim greatestVolume As LongLong

    
        


    'Initialize the greatest volume variable
    greatestVolume = 0

    'Loop through the stock data range
    For i = 2 To 3002

        'If the current stock's volume is greater than the greatest volume, update the greatest volume variable and the stock with the greatest volume variable
        If ws.Cells(i, 12).Value > greatestVolume Then
            greatestVolume = ws.Cells(i, 12).Value
            stockWithGreatestVolume = ws.Cells(i, 9).Value
        End If

    Next i

    'Print the stock with the greatest volume and its volume in the specified columns
    ws.Range("P4").Value = stockWithGreatestVolume
    ws.Range("Q4").Value = greatestVolume
    
    
    
    
    Dim stockWithGreatestincrease As String
    Dim greatestincrease As Double
    
    'Initialize the greatest volume variable
    greatestincrease = 0

    'Loop through the stock data range
    For i = 2 To 3002

        'If the current stock's volume is greater than the greatest volume, update the greatest volume variable and the stock with the greatest volume variable
        If ws.Cells(i, 11).Value > greatestincrease Then
            greatestincrease = ws.Cells(i, 11).Value
            stockWithGreatestincrease = ws.Cells(i, 9).Value
        End If

    Next i

    'Print the stock with the greatest volume and its volume in the specified columns
    ws.Range("P2").Value = stockWithGreatestincrease
    ws.Range("Q2").Value = greatestincrease



    Dim stockWithGreatestdecrease As String
    Dim greatestdecrease As Double

    
    'Initialize the greatest volume variable
    greatestdecrease = 0

    'Loop through the stock data range
    For i = 2 To 3002

        'If the current stock's volume is greater than the greatest volume, update the greatest volume variable and the stock with the greatest volume variable
        If ws.Cells(i, 11).Value < greatestdecrease Then
            greatestdecrease = ws.Cells(i, 11).Value
            stockWithGreatestdecrease = ws.Cells(i, 9).Value
        End If

    Next i

    'Print the stock with the greatest volume and its volume in the specified columns
    ws.Range("P3").Value = stockWithGreatestdecrease
    ws.Range("Q3").Value = greatestdecrease
    
    Next ws
    
 
End Sub

