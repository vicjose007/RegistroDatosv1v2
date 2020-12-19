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

Console.WriteLine("Seleccione la opcion que desee\n" + "1) Registrar");

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

}

}

}

}
```