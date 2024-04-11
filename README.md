# ProyectoJava
Mi proyecto se realizo en Java Netbeans con la finalidad de calcular los triangulos, sus vertices

import java.util.Scanner;


public class TrianguloEvaluar {
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Ingrese las coordenadas de los vértices del triángulo:");
        System.out.print("Vértice 1 (x1 y1): ");
        double x1 = scanner.nextDouble();
        double y1 = scanner.nextDouble();
        
        System.out.print("Vértice 2 (x2 y2): ");
        double x2 = scanner.nextDouble();
        double y2 = scanner.nextDouble();
        
        System.out.print("Vértice 3 (x3 y3): ");
        double x3 = scanner.nextDouble();
        double y3 = scanner.nextDouble();
        
        double lado1 = distanciaEntrePuntos(x1, y1, x2, y2);
        double lado2 = distanciaEntrePuntos(x2, y2, x3, y3);
        double lado3 = distanciaEntrePuntos(x3, y3, x1, y1);
        
        double perimetro = calcularPerimetro(lado1, lado2, lado3);
        double area = calcularArea(lado1, lado2, lado3);
        
        double[] angulos = calcularAngulos(lado1, lado2, lado3);
        
        String tipoTriangulo = determinarTipoTriangulo(lado1, lado2, lado3);
        
        System.out.println("Perímetro: " + perimetro);
        System.out.println("Área: " + area);
        System.out.println("Ángulo 1: " + angulos[0]);
        System.out.println("Ángulo 2: " + angulos[1]);
        System.out.println("Ángulo 3: " + angulos[2]);
        System.out.println("Tipo de triángulo: " + tipoTriangulo);
    }
    
    public static double distanciaEntrePuntos(double x1, double y1, double x2, double y2) {
        return Math.sqrt(Math.pow(x2 - x1, 2) + Math.pow(y2 - y1, 2));
    }
    //pow elevar una potencia
    //ToDegress radianes a grados
    //acos arco coseno
    //sqrt raiz cubo
    public static double calcularPerimetro(double lado1, double lado2, double lado3) {
        return lado1 + lado2 + lado3;
    }
    
    public static double calcularArea(double lado1, double lado2, double lado3) {
        double s = (lado1 + lado2 + lado3) / 2;
        return Math.sqrt(s * (s - lado1) * (s - lado2) * (s - lado3));
    }
    
    public static double[] calcularAngulos(double lado1, double lado2, double lado3) {
        double[] angulos = new double[3];
        angulos[0] = Math.toDegrees(Math.acos((lado2 * lado2 + lado3 * lado3 - lado1 * lado1) / (2 * lado2 * lado3)));
        angulos[1] = Math.toDegrees(Math.acos((lado1 * lado1 + lado3 * lado3 - lado2 * lado2) / (2 * lado1 * lado3)));
        angulos[2] = Math.toDegrees(Math.acos((lado1 * lado1 + lado2 * lado2 - lado3 * lado3) / (2 * lado1 * lado2)));
        return angulos;
    }
    
    public static String determinarTipoTriangulo(double lado1, double lado2, double lado3) {
        if (lado1 == lado2 && lado2 == lado3) {
            return "Equilátero";
        } else if (lado1 == lado2 || lado1 == lado3 || lado2 == lado3) {
            return "Isósceles";
        } else {
            return "Escaleno";
        }
    }
}
