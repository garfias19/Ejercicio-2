# Ejercicio-2
El Generador de Contraseñas Seguras es una herramienta en línea de comandos diseñada para crear contraseñas aleatorias y seguras. Permite a los usuarios personalizar las contraseñas generadas en función de sus necesidades específicas de seguridad, eligiendo entre varios tipos de caracteres.

## Solicitar la longuitud de la contraseña
```kotlin
using System;
using System.Text;

class Program
{
    static void Main()
    {
        Console.WriteLine("Generador de Contraseñas");
        Console.Write("Introduce la longitud deseada para la contraseña: ");
        int longitud = Convert.ToInt32(Console.ReadLine());
```
## Solicitar los tipos de caracteres incluir
```kotlin
        Console.Write("¿Incluir letras mayúsculas? (s/n): ");
        bool incluirMayusculas = Console.ReadLine().ToLower() == "s";
        
        Console.Write("¿Incluir letras minúsculas? (s/n): ");
        bool incluirMinusculas = Console.ReadLine().ToLower() == "s";
        
        Console.Write("¿Incluir números? (s/n): ");
        bool incluirNumeros = Console.ReadLine().ToLower() == "s";
        
        Console.Write("¿Incluir símbolos especiales? (s/n): ");
        bool incluirSimbolos = Console.ReadLine().ToLower() == "s";

```
## Generar la contraseña y mostrar
```kotlin
        string contrasena = GenerarContrasena(longitud, incluirMayusculas, incluirMinusculas, incluirNumeros, incluirSimbolos);
        Console.WriteLine("Contraseña generada: " + contrasena);
    }
    
    static string GenerarContrasena(int longitud, bool incluirMayusculas, bool incluirMinusculas, bool incluirNumeros, bool incluirSimbolos)
    {
```
## Definir los posibles caracteres para cada tipo 
```kotlin
        const string caracteresMayusculas = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        const string caracteresMinusculas = "abcdefghijklmnopqrstuvwxyz";
        const string caracteresNumeros = "0123456789";
        const string caracteresSimbolos = "!@#$%^&*()_+[]{}|;:,.<>?";
```
## Crear un conjunto de caracteres posibles y verificar que se han seleccionado
```kotlin
        StringBuilder caracteresPosibles = new StringBuilder();
        if (incluirMayusculas) caracteresPosibles.Append(caracteresMayusculas);
        if (incluirMinusculas) caracteresPosibles.Append(caracteresMinusculas);
        if (incluirNumeros) caracteresPosibles.Append(caracteresNumeros);
        if (incluirSimbolos) caracteresPosibles.Append(caracteresSimbolos);
        
        if (caracteresPosibles.Length == 0)
        {
            throw new ArgumentException("Debe incluir al menos un tipo de carácter.");
        }
```
## Generar la contraseña aleatoria 
```kotlin
        Random rng = new Random();
        char[] contrasena = new char[longitud];
        for (int i = 0; i < longitud; i++)
        {
            contrasena[i] = caracteresPosibles[rng.Next(caracteresPosibles.Length)];
        }

        return new string(contrasena);
    }
}
```
![image](https://github.com/user-attachments/assets/f5a11fd3-0864-40c9-9601-7a33575ff9a0)
