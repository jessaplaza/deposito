# deposito
Tarea ED04
package cuentas;

/**
 * Esta clase para ingresar un saldo
 * 
 * @author jessica de la plaza
 * @version 2.0
 *
 *  */
public class CCuenta {

    /**
     * @return the nombre
     */
    public String getNombre() {
        return nombre;
    }

    /**
     * @param nombre the nombre to set
     */
    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    /**
     * @return the cuenta
     */
    public String getCuenta() {
        return cuenta;
    }

    /**
     * @param cuenta the cuenta to set
     */
    public void setCuenta(String cuenta) {
        this.cuenta = cuenta;
    }

    /**
     * @return the saldo
     */
    public double getSaldo() {
        return saldo;
    }

    /**
     * @param saldo the saldo to set
     */
    public void setSaldo(double saldo) {
        this.saldo = saldo;
    }

    /**
     * @return the tipoInterés
     */
    public double getTipoInterés() {
        return tipoInterés;
    }

    /**
     * @param tipoInterés the tipoInterés to set
     */
    public void setTipoInterés(double tipoInterés) {
        this.tipoInterés = tipoInterés;
    }


    private String nombre;
    private String cuenta;
    private double saldo;
    private double tipoInterés;

    public CCuenta()
    {
    }

    public CCuenta(String nom, String cue, double sal, double tipo)
    {
        nombre =nom;
        cuenta=cue;
        saldo=sal;
    }

    public double estado()
    {
        return getSaldo();
    }

    public void ingresar(double cantidad) throws Exception
    {
        if (cantidad<0)
            throw new Exception("No se puede ingresar una cantidad negativa");
        setSaldo(getSaldo() + cantidad);
    }

    public void retirar(double cantidad) throws Exception
    {
        if (cantidad <= 0)
            throw new Exception ("No se puede retirar una cantidad negativa");
        if (estado()< cantidad)
            throw new Exception ("No se hay suficiente saldo");
        setSaldo(getSaldo() - cantidad);
    }
    public class Main {

        public static void main(String[] args) {
        	operativa_cuenta();
             }
        public static void operativa_cuenta() {
        	float cantidad;
            CCuenta cuenta1;
            double saldoActual;

            cuenta1 = new CCuenta("Antonio López","1000-2365-85-1230456789",2500,0);
            saldoActual = cuenta1.estado();
            System.out.println("El saldo actual es"+ saldoActual );

            try {
                cuenta1.retirar(2300);
            } catch (Exception e) {
                System.out.print("Fallo al retirar");
            }
            try {
                System.out.println("Ingreso en cuenta");
                cuenta1.ingresar(695);
            } catch (Exception e) {
                System.out.print("Fallo al ingresar");
            }
        }
    }

}
