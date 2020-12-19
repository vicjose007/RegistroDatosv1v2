```c#
using System;

using System.IO;

using System.Collections.Generic;

using System.Threading.Tasks;

using System.Text;

namespace registro

{

class Program

{

static void Main(string[] args)

{

Console.WriteLine("Seleccione la opcion que desee\n";

+ "1) Registrar\n&quot; + &quot;2) Buscar a travez de la Cedula \n"+ "3) Lista\n");

int Select = int.Parse(Console.ReadLine());

switch(Select)

{

case 1:

Console.Clear();

Console.WriteLine("Ingrese los datos sugeridos \n" + "Nombre, Apellido, Edad, Cedula (Separar cada una con una (,)");

string Data = Console.ReadLine();

try

{

using(Stream datos = new FileStream("C:/Users/vicjo/OneDrive/Desktop/RegistroDatos/registro.csv",FileMode.Append,FileAccess.Write))

{

using(StreamWriter output = new StreamWriter(datos))

{

output.WriteLine(Data);

}

}

}

catch(Exception ex)

{

Console.WriteLine(ex.Message);

}

break;

case 2:

{

FileStream insideFile = new FileStream("C:/Users/vicjo/OneDrive/Desktop/RegistroDatos/registro.csv", FileMode.Open, FileAccess.Read);

StreamReader reader = new StreamReader(insideFile);

string save;

string cedula;

Console.WriteLine("Ingrese la cedula porfavor: ");

cedula = Console.ReadLine();

try

{

save = reader.ReadLine();

while(save != null)

{

if(save.Contains(cedula))

{

Console.WriteLine(save);

}

save = reader. ReadLine();

}

}

finally

{

reader.Close();

insideFile.Close();

}

}

break;

case 3:

Console.Clear();

Stream lst = new FileStream("C:/Users/vicjo/OneDrive/Desktop/RegistroDatos/registro.csv", FileMode.Open, FileAccess.Read);

StreamReader file = new StreamReader(lst);

while(!file.EndOfStream)

{

Console.WriteLine(file.ReadLine());

}

break;

}

}

}

}
```

