# Date fix for AS/400 Dates
## For use in Trifacta

### Current Date Format

#### Dates > 01-01-2000
1000101 --> [1] 21st century [00] Year [01] Month [01] Day

#### Dates < 12-31-1999
991231 --> [99] Year [12] Month [31] Day

## Change Req_Date to Usable Date
```
replace col: Req_Date with: '' on: `{start}1`
derive value: 20 as: 'Req_Date_Century'
merge col: Req_Date_Century,Req_Date as: 'Req_Date_full'
drop col: Req_Date,Req_Date_Century
```

---
## Change Date Last Invoiced to Usable Date
```
replace col: Date_Last_Invoiced with: '' on: `{start}1`
derive value: 20 as: 'Date_Last_Invoiced_Century'
merge col: Date_Last_Invoiced_Century,Date_Last_Invoiced as: 'Date_Last_Invoiced_full'
drop col: Date_Last_Invoiced,Date_Last_Invoiced_Century
```
