# evaluacion-
calcular las coordenadas para posteriormente verificar el tipo de tringulo escaleno, isoceles, equilatero
import java.util.Scanner;

public class TipoTriangulo {
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Pedir las coordenadas de los vértices del triángulo
        System.out.println("Introduce las coordenadas (x, y) para el vértice 1:");
        double x1 = scanner.nextDouble();
        double y1 = scanner.nextDouble();
        
        System.out.println("Introduce las coordenadas (x, y) para el vértice 2:");
        double x2 = scanner.nextDouble();
        double y2 = scanner.nextDouble();
        
        System.out.println("Introduce las coordenadas (x, y) para el vértice 3:");
        double x3 = scanner.nextDouble();
        double y3 = scanner.nextDouble();
        
        // Calcular las longitudes de los lados
        double lado1 = Math.sqrt(Math.pow(x2 - x1, 2) + Math.pow(y2 - y1, 2));
        double lado2 = Math.sqrt(Math.pow(x3 - x2, 2) + Math.pow(y3 - y2, 2));
        double lado3 = Math.sqrt(Math.pow(x1 - x3, 2) + Math.pow(y1 - y3, 2));
        
        // Calcular el perímetro
        double perimetro = lado1 + lado2 + lado3;
        
        // Calcular el área usando la fórmula de Herón
        double semiperimetro = perimetro / 2;
        double area = Math.sqrt(semiperimetro * (semiperimetro - lado1) * (semiperimetro - lado2) * (semiperimetro - lado3));
        
        // Calcular los ángulos
        double angulo1 = Math.acos((Math.pow(lado2, 2) + Math.pow(lado3, 2) - Math.pow(lado1, 2)) / (2 * lado2 * lado3));
        double angulo2 = Math.acos((Math.pow(lado1, 2) + Math.pow(lado3, 2) - Math.pow(lado2, 2)) / (2 * lado1 * lado3));
        double angulo3 = Math.acos((Math.pow(lado1, 2) + Math.pow(lado2, 2) - Math.pow(lado3, 2)) / (2 * lado1 * lado2));
        
        // Convertir los ángulos de radianes a grados
        angulo1 = Math.toDegrees(angulo1);
        angulo2 = Math.toDegrees(angulo2);
        angulo3 = Math.toDegrees(angulo3);
        
        // Determinar el tipo de triángulo
        String tipoTriangulo;
        if (lado1 == lado2 && lado2 == lado3) {
            tipoTriangulo = "Equilátero";
        } else if (lado1 == lado2 || lado1 == lado3 || lado2 == lado3) {
            tipoTriangulo = "Isósceles";
        } else {
            tipoTriangulo = "Escaleno";
        }
        
        // Mostrar resultados
        System.out.println("Tipo de triángulo: " + tipoTriangulo);
        System.out.println("Perímetro: " + perimetro);
        System.out.println("Área: " + area);
        System.out.println("Ángulo 1: " + angulo1);
        System.out.println("Ángulo 2: " + angulo2);
        System.out.println("Ángulo 3: " + angulo3);
        
        scanner.close();
    }
}
