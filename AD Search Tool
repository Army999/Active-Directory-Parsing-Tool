PowerShell.exe -windowstyle hidden {AD Search Tool.ps1}

Add-Type -assembly System.Windows.Forms

$main_form = New-Object System.Windows.Forms.Form

$main_form.Text ='AD Search Tool'

$main_form.Width = 600

$main_form.Height = 400

$main_form.AutoSize = $true

 

$Label =New-Object System.Windows.Forms.Label

$Label.Text ="AD Users"

$Label.Location =New-Object System.Drawing.Point(0,10)

$Label.AutoSize =$true

$main_form.Controls.Add($Label)

 

$ComboBox = New-Object System.Windows.Forms.ComboBox

$ComboBox.Width = 300

$Users = Get-ADUser -Filter 'enabled -eq $true' -Properties mail |

    Select-Object -Property Name,samaccountname,mail

Foreach ($User in $Users)

{

$ComboBox.Items.Add($User.SamAccountName);

}

$ComboBox.Location  = New-Object System.Drawing.Point(60,10)

$main_form.Controls.Add($ComboBox)

 

$Label2 = New-Object System.Windows.Forms.Label

$Label2.Text = "Last Password Set:"

$Label2.Location  = New-Object System.Drawing.Point(0,40)

$Label2.AutoSize = $true

$main_form.Controls.Add($Label2)

$Label3 = New-Object System.Windows.Forms.Label

$Label3.Text = ""

$Label3.Location  = New-Object System.Drawing.Point(115,40)

$Label3.AutoSize = $true

$main_form.Controls.Add($Label3)

 

$Label4 = New-Object System.Windows.Forms.Label

$Label4.Text = "Last Login:"

$Label4.Location  = New-Object System.Drawing.Point(0,60)

$Label4.AutoSize = $true

$main_form.Controls.Add($Label4)

$Label5 = New-Object System.Windows.Forms.Label

$Label5.Text = ""

$Label5.Location  = New-Object System.Drawing.Point(115,60)

$Label5.AutoSize = $true

$main_form.Controls.Add($Label5)

 

$Label6 = New-Object System.Windows.Forms.Label

$Label6.Text = "Bad Password Time:"

$Label6.Location  = New-Object System.Drawing.Point(0,80)

$Label6.AutoSize = $true

$main_form.Controls.Add($Label6)

$Label7 = New-Object System.Windows.Forms.Label

$Label7.Text = ""

$Label7.Location  = New-Object System.Drawing.Point(115,80)

$Label7.AutoSize = $true

$main_form.Controls.Add($Label7)

 

$Label8 = New-Object System.Windows.Forms.Label

$Label8.Text = "Bad Password Count:"

$Label8.Location  = New-Object System.Drawing.Point(0,100)

$Label8.AutoSize = $true

$main_form.Controls.Add($Label8)

$Label9 = New-Object System.Windows.Forms.Label

$Label9.Text = ""

$Label9.Location  = New-Object System.Drawing.Point(115,100)

$Label9.AutoSize = $true

$main_form.Controls.Add($Label9)

 

$Label10 = New-Object System.Windows.Forms.Label

$Label10.Text = "User ID:"

$Label10.Location  = New-Object System.Drawing.Point(0,120)

$Label10.AutoSize = $true

$main_form.Controls.Add($Label10)

$Label11 = New-Object System.Windows.Forms.Label

$Label11.Text = ""

$Label11.Location  = New-Object System.Drawing.Point(115,120)

$Label11.AutoSize = $true

$main_form.Controls.Add($Label11)

 

$Button = New-Object System.Windows.Forms.Button

$Button.Location = New-Object System.Drawing.Size(400,10)

$Button.Size = New-Object System.Drawing.Size(120,23)

$Button.Text = "Check"

$main_form.Controls.Add($Button)

 

$Button.Add_Click(

{

$Label3.Text = [datetime]::FromFileTime((Get-ADUser -identity $ComboBox.selectedItem -Properties pwdLastSet).pwdLastSet).ToString()

$Label5.Text = [datetime]::FromFileTime((Get-ADUser -identity $ComboBox.selectedItem -Properties lastLogon).lastLogon).ToString()

$Label7.Text = [datetime]::FromFileTime((Get-ADUser -identity $ComboBox.selectedItem -Properties badPasswordTime).badPasswordTime).ToString()

$Label9.Text = ((Get-ADUser -identity $ComboBox.selectedItem -Properties badPwdCount).badPwdCount).ToString()

$Label11.Text = ((Get-ADUser -Identity $ComboBox.SelectedItem -Properties employeeID).employeeID).ToString()

}

)

 

 

$main_form.ShowDialog()
