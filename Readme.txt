1 введение
1 1 область применения
1 2 краткое описание возможностей
1 3 уровень подготовки пользователя
1 4 перечень эксплуатационной документации
2 назначение и условия применения
2 1 виды деятельности, функции
2 2 программные и аппаратные требования к системе
3 подготовка к работе
3 1 состав дистрибутива
3 2 запуск системы
3 3 проверка работоспособности системы
4 описание операций
4 1 1 наименование операций
4 1 2 условие выполнения операций
4 1 3 подготовительные действия
4 1 4 основные действия
4 1 5 заключительные действия
4 1 6 ресурсы расходуемые на операцию
5 аварийные ситуации




ВХОД
using (OleDbConnection connection = new OleDbConnection(@"Provider = Microsoft.ACE.OLEDB.12.0; Data Source = prepod.accdb"))
{
    string query = "SELECT Role FROM Users WHERE Login = ? AND Password = ?";
    using (OleDbCommand command = new OleDbCommand(query, connection))
    {
        command.Parameters.AddWithValue("?", tbLogin.Text);
        command.Parameters.AddWithValue("?", tbPass.Text);
        connection.Open();
        object result = command.ExecuteScalar();
        if (result != null)
        {
            string role = result.ToString();
            Hide();
            Form1 mf = new Form1();
            if (role == "User")
            {
                mf.button1.Visible = false;
                mf.button2.Visible = false;
            }
            mf.Show();
        }
        else
        {
            MessageBox.Show("Неверный логин или пароль♠");
        }
    }
}


РЕГИСТРАЦИЯ
Form1 main = this.Owner as Form1;
if (main != null)
{
    DataRow nRow = main.prepodDataSet.Tables[4].NewRow();
    int rc = main.dataGridView1.RowCount + 1;
    nRow[0] = rc;
    nRow[1] = tbLogin.Text;
    nRow[2] = tbPass.Text;
    main.prepodDataSet.Tables[4].Rows.Add(nRow);
    main.usersTableAdapter.Update(main.prepodDataSet.Users);
    main.prepodDataSet.Tables[4].AcceptChanges();
    main.dataGridView1.Refresh();
    tbLogin.Text = "";
    tbPass.Text = "";

}


КНОПКА СОХРАНИТЬ
            преподавателиTableAdapter.Update(prepodDataSet);
            должностиTableAdapter.Update(prepodDataSet);
            предметыTableAdapter.Update(prepodDataSet);
            занятияTableAdapter.Update(prepodDataSet);
            dataGridView1.Refresh();
            dataGridView2.Refresh();
            dataGridView3.Refresh();
            dataGridView4.Refresh();

ДОБАВИТЬ ЗАПИСЬ
if (tabControl1.SelectedIndex == 0)
{
    addPrepod af = new addPrepod();
    af.Owner = this;
    af.Show();
}
else if (tabControl1.SelectedIndex == 1)
{
    addDolzh af = new addDolzh();
    af.Owner = this;
    af.Show();
}

ПОИСК ЗАПИСИ
if (string.IsNullOrEmpty(tbStr.Text))
{
    MessageBox.Show("Введите поиск");
}
Form1 main = this.Owner as Form1;

if (main != null)
{
    if (main.tabControl1.SelectedIndex == 0)
    {
        for (int i = 0; i < main.dataGridView1.RowCount; i++)
        {
            main.dataGridView1.Rows[i].Selected = false;
            for (int j = 0; j < main.dataGridView1.ColumnCount; j++)
                if (main.dataGridView1.Rows[i].Cells[j].Value != null)
                    if (main.dataGridView1.Rows[i].Cells[j].Value.ToString().Contains(tbStr.Text))
                    {
                        main.dataGridView1.Rows[i].Selected = true;
                        break;
                    }
        }
    }
    else if (main.tabControl1.SelectedIndex == 1)
    {
        for (int i = 0; i < main.dataGridView2.RowCount; i++)
        {
            main.dataGridView2.Rows[i].Selected = false;
            for (int j = 0; j < main.dataGridView2.ColumnCount; j++)
                if (main.dataGridView2.Rows[i].Cells[j].Value != null)
                    if (main.dataGridView2.Rows[i].Cells[j].Value.ToString().Contains(tbStr.Text))
                    {
                        main.dataGridView2.Rows[i].Selected = true;
                        break;
                    }
        }
    }
    else if (main.tabControl1.SelectedIndex == 2)
    {
        for (int i = 0; i < main.dataGridView3.RowCount; i++)
        {
            main.dataGridView3.Rows[i].Selected = false;
            for (int j = 0; j < main.dataGridView3.ColumnCount; j++)
                if (main.dataGridView3.Rows[i].Cells[j].Value != null)
                    if (main.dataGridView3.Rows[i].Cells[j].Value.ToString().Contains(tbStr.Text))
                    {
                        main.dataGridView3.Rows[i].Selected = true;
                        break;
                    }
        }
    }
    else if (main.tabControl1.SelectedIndex == 3)
    {
        for (int i = 0; i < main.dataGridView4.RowCount; i++)
        {
            main.dataGridView4.Rows[i].Selected = false;
            for (int j = 0; j < main.dataGridView4.ColumnCount; j++)
                if (main.dataGridView4.Rows[i].Cells[j].Value != null)
                    if (main.dataGridView4.Rows[i].Cells[j].Value.ToString().Contains(tbStr.Text))
                    {
                        main.dataGridView4.Rows[i].Selected = true;
                        break;
                    }
        }
    }
}

ПЕРЕХОД ПО ФОРМЕ
            logForm sf = new logForm();
            sf.Owner = this;
            sf.Show();


ОКОНЧАТЕЛЬНОЕ ДОБАВЛЕНИЕ В БД ПОСЛЕ ВВОДА ДАННЫХ 
Form1 main = this.Owner as Form1;
if (main != null)
{
    DataRow nRow = main.prepodDataSet.Tables[0].NewRow();
    int rc = main.dataGridView1.RowCount + 1;
    nRow[0] = rc;
    nRow[1] = tbFam.Text;
    nRow[2] = tbName.Text;
    nRow[3] = tbOt.Text;
    nRow[4] = tbPhone.Text;
    nRow[5] = tbWork.Text;
    nRow[6] = tbAdress.Text;
    nRow[7] = tbHar.Text;
    main.prepodDataSet.Tables[0].Rows.Add(nRow);
    main.преподавателиTableAdapter.Update(main.prepodDataSet.Преподаватели);
    main.prepodDataSet.Tables[0].AcceptChanges();
    main.dataGridView1.Refresh();
    tbFam.Text = "";
    tbName.Text = "";
    tbOt.Text = "";
    tbPhone.Text = "";
    tbWork.Text = "";
    tbAdress.Text = "";
    tbHar.Text = "";
}
