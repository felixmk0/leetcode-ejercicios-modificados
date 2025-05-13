![GitHub Repo stars](https://img.shields.io/github/stars/felixmk0/leetcode-ejercicios-modificados)
![GitHub watchers](https://img.shields.io/github/watchers/felixmk0/leetcode-ejercicios-modificados)
![GitHub forks](https://img.shields.io/github/forks/felixmk0/leetcode-ejercicios-modificados)

# 📘 Ejercicios de LeetCode Modificados

Este repositorio contiene una colección de problemas de **LeetCode** modificados y adaptados, con enunciados en español y soluciones en **Java**. Los ejercicios están organizados por niveles de dificultad y cada uno incluye casos de prueba, explicaciones y análisis de la solución.

**⚠️ Nota:** Estos ejercicios están implementados en **Java** para fines de práctica personal. Algunas soluciones pueden contener malas prácticas de programación o no estar optimizadas, ya que aún estoy aprendiendo. ¡Cualquier mejora es bienvenida!

---

## Índice

- [🟠 Medio](#medio)

---

## 🟠 Medio

### 001 - Transformaciones en una String

**Enunciado:**

Estás dado una cadena `s` y un número entero `t`, que representa el número de transformaciones que se deben realizar. En cada transformación, cada carácter de `s` se reemplaza de acuerdo con las siguientes reglas:

1. Si el carácter es `'z'`, reemplázalo con la cadena `"ab"`.
2. Si no es `'z'`, reemplázalo por el siguiente carácter en el alfabeto (por ejemplo, `'a'` se convierte en `'b'`, `'b'` se convierte en `'c'`, etc.).

Muestra la cadena resultante de cada transformación, con su longitud y nr. de transformación.


**Ejemplos:**

![image](https://github.com/user-attachments/assets/ca677a56-83e3-498b-b249-229e65e65514)

![image](https://github.com/user-attachments/assets/faf2f4ee-4363-4b00-b765-a758775f6d4b)

### Mi solución:

<details>
  <summary>Haz clic aquí para ver la solución </summary>

```java
public class Solution {

    public static void main(String[] args) {
        transformString("abcyy", 2);
    }

    public static void transformString(String s, int t) {
        for (int i = 0; i < t; i++) {
            for (int j = 0; j < s.length(); j++) {
                if (s.charAt(j) == 'z') {
                    if (j != 0) {
                        s = s.substring(0, j) + "ab" + s.substring(j + 1);
                        j++;
                    } else s = "ab" + s.substring(j + 1);
                } else {
                    if (j != 0) s = s.substring(0, j) + getNextChar(s.charAt(j)) + s.substring(j + 1);
                    else s = getNextChar(s.charAt(j)) + s.substring(j + 1);
                }
            }
            System.out.println("T = " + i + ", String = " + s + ", Length: " + s.length());
        }
    }


    public static char getNextChar(char c) {
        if (c == 'z') return 'a';
        return (char) (c + 1);
    }
}
```
</details>
