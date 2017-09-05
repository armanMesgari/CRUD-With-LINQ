Introduction

In this chapter we want  to add, Update and Delete Data From Database With LINQ Connection.

__________________________________________________________________________

Process

The following steps show how to Create, Read, Update and Delete Data from Database with LINQ Connection:

1. First, Click New Project in Start Page or On File Menu.

2. In New Project Dialog, Click Windows On Left Pane and Windows Forms Application On Middle Pane.

3. First, using System.LINQ:
using System.Linq;


4. In The Click Event of add Button Write this Code:

if (txt_Name.Text.Replace(" ", "") != "" || txt_LastName.Text.Replace(" ", "") != "") 
 
{ 
 
    DialogResult dr = MessageBox.Show("Do you Want To Add ?", "CRUD",      MessageBoxButtons.YesNo, MessageBoxIcon.Question); 
 
        if (dr == DialogResult.Yes) 
 
        { 
 
            DbDataContext dbdc = new DbDataContext(); 
 
            tbl_Student tbls = new tbl_Student() 
 
             { 
 
                  S_Name = txt_Name.Text, 
 
                 S_LastName = txt_LastName.Text, 
 
                 S_NationalCode = txt_NationalCode.Text 
 
        }; 
 
            dbdc.tbl_Students.InsertOnSubmit(tbls); 
 
            dbdc.SubmitChanges(); 
 
            dgv_Data.DataSource = dbdc.tbl_Students; 
 
            S_ID = ""; 
 
            Clear(); 
 
    } 
 
} 
 
else 
 
{ 
 
    if (txt_Name.Text.Replace(" ", "") != "") 
 
       { 
 
        MessageBox.Show("Please enter Student Name", "CRUD",          MessageBoxButtons.OK, MessageBoxIcon.Information); 
 
               txt_Name.Focus(); 
 
       } 
 
    else 
 
        { 
 
            MessageBox.Show("Please enter Student Lastname", "CRUD",          MessageBoxButtons.OK, MessageBoxIcon.Information); 
 
                txt_LastName.Focus(); 
 
        } 
 }
 
5. In The Click Event of edit Button Write this Code:

            if (txt_Name.Text.Replace(" ", "") != "" || txt_LastName.Text.Replace(" ", "") != "") 
 
            { 
 
                DialogResult dr = MessageBox.Show("Do you Want To Edit ?", "CRUD", MessageBoxButtons.YesNo, MessageBoxIcon.Question); 
 
                if (dr == DialogResult.Yes) 
 
                { 
 
                    DbDataContext dbdc = new DbDataContext(); 
 
                    var Edit = dbdc.tbl_Students.Where(tbl_Students => tbl_Students.S_ID == int.Parse(S_ID)).Single(); 
 
                    Edit.S_Name = txt_Name.Text; 
 
                    Edit.S_LastName = txt_LastName.Text; 
 
                    Edit.S_NationalCode = txt_NationalCode.Text; 
 
                    dbdc.SubmitChanges(); 
 
                    dgv_Data.DataSource = dbdc.tbl_Students; 
 
                    S_ID = ""; 
 
                    Clear(); 
 
                } 
 
            } 
 
            else 
 
            { 
 
                if (txt_Name.Text.Replace(" ", "") != "") 
 
                { 
 
                    MessageBox.Show("Please enter Student Name", "CRUD", MessageBoxButtons.OK, MessageBoxIcon.Information); 
 
                    txt_Name.Focus(); 
 
                } 
 
                else 
 
                { 
 
                    MessageBox.Show("Please enter Student Lastname", "CRUD", MessageBoxButtons.OK, MessageBoxIcon.Information); 
 
                    txt_LastName.Focus(); 
 
                } 
 
            }

6. In The Click Event of delete Button Write this Code:

if (txt_Name.Text.Replace(" ", "") != "" || txt_LastName.Text.Replace(" ", "") != "") 
 
            { 
 
                DialogResult dr = MessageBox.Show("Do you Want To Delete This Row ?", "CRUD", MessageBoxButtons.YesNo, MessageBoxIcon.Question); 
 
                if (dr == DialogResult.Yes) 
 
                { 
 
                    DbDataContext dbdc = new DbDataContext(); 
 
                    var Delete = dbdc.tbl_Students.Where(tbl_Students => tbl_Students.S_ID == int.Parse(S_ID)).Single(); 
 
                    dbdc.tbl_Students.DeleteOnSubmit(Delete); 
 
                    dbdc.SubmitChanges(); 
 
                    dgv_Data.DataSource = dbdc.tbl_Students; 
 
                    S_ID = ""; 
 
                    Clear(); 
 
                } 
 
            } 
 
            else 
 
            { 
 
                if (txt_Name.Text.Replace(" ", "") != "") 
 
                { 
 
                    MessageBox.Show("Please enter Student Name", "CRUD", MessageBoxButtons.OK, MessageBoxIcon.Information); 
 
                    txt_Name.Focus(); 
 
                } 
 
                else 
 
                { 
 
                    MessageBox.Show("Please enter Student Lastname", "CRUD", MessageBoxButtons.OK, MessageBoxIcon.Information); 
 
                    txt_LastName.Focus(); 
 
                } 
 
            }


Good Luck!

More Information

My Email-Address is armanmesgari@outlook.com

To open this sample, you'll need Visual Studio 2015.

This Is Github Link : github.com/armanMesgari/CRUD-With-LINQ

----------------------------------------------------------------------------------------

Please Write Your Sight About this Sample.
