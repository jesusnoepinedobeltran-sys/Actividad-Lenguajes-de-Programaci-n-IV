# Actividad-Lenguajes-de-Programaci-n-IV
Programa Banco Mexicano
private void jbtnContinuarActionPerformed(java.awt.event.ActionEvent evt) {
    // TODO add your handling code here:
    String opcion = jtfOpcion.getText();

    switch (opcion) {
        case "1":
            DepositoJFrame deposito = new DepositoJFrame();
            deposito.show();
            break; // Se agrega break faltante
        case "2":
            RetiroJFrame retiro = new RetiroJFrame();
            retiro.show();
            break; // Se agrega break faltante
        case "3":
            SaldoJFrame saldo = new SaldoJFrame();
            saldo.show();
            break; // Se agrega break faltante
        case "4":
            this.dispose();
            break;
        default:
            JOptionPane.showMessageDialog(null, "Opción no válida...");
            break;
    }
}




public class CuentaBancaria {
    // El atributo static permite que el saldo se comparta entre todas las ventanas
    private static double saldo = 0.0;

    // Método para depositar
    public void depositar(double cantidad) {
        if (cantidad > 0) {
            saldo += cantidad;
        }
    }

    // Método para retirar
    public void retirar(double cantidad) {
        // Valida que no retire más de lo que tiene
        if (cantidad > 0 && cantidad <= saldo) {
            saldo -= cantidad;
        } else {
            javax.swing.JOptionPane.showMessageDialog(null, "Saldo insuficiente o cantidad inválida.");
        }
    }

    // Método para consultar el saldo
    public double getSaldo() {
        return saldo;
    }
}


try {
    // 1. Obtener la cantidad de la caja de texto (asegúrate de que tu variable se llame txtCantidad)
    double cantidad = Double.parseDouble(txtCantidad.getText());

    // 2. Aplicar POO: Crear el objeto y usar su método
    CuentaBancaria cuenta = new CuentaBancaria();
    cuenta.depositar(cantidad);

    // 3. Preguntar si desea realizar otro depósito
    int respuesta = javax.swing.JOptionPane.showConfirmDialog(this, 
            "¿Desea realizar otro depósito?", 
            "Depósito Exitoso", 
            javax.swing.JOptionPane.YES_NO_OPTION);

    // 4. Validar la respuesta
    if (respuesta == javax.swing.JOptionPane.YES_OPTION) {
        // Si elige "Sí", solo limpiamos la caja de texto para que vuelva a capturar
        txtCantidad.setText("");
    } else {
        // Si elige "No", cerramos esta ventana para que regrese al menú principal
        this.dispose(); 
    }

} catch (NumberFormatException ex) {
    javax.swing.JOptionPane.showMessageDialog(this, "Por favor, ingresa una cantidad numérica válida.");
}


try {
    // 1. Obtener el monto a retirar (asegúrate de que tu variable se llame txtMonto)
    double cantidad = Double.parseDouble(txtMonto.getText());

    // 2. Aplicar POO
    CuentaBancaria cuenta = new CuentaBancaria();
    
    // Opcional: Validar antes de retirar si hay saldo suficiente para no cerrar la ventana si hay error
    if (cantidad <= cuenta.getSaldo()) {
        cuenta.retirar(cantidad);
        javax.swing.JOptionPane.showMessageDialog(this, "Retiro exitoso.");
        // Cerrar ventana y regresar al menú principal
        this.dispose();
    } else {
        javax.swing.JOptionPane.showMessageDialog(this, "Saldo insuficiente para realizar el retiro.");
    }

} catch (NumberFormatException ex) {
    javax.swing.JOptionPane.showMessageDialog(this, "Por favor, ingresa una cantidad numérica válida.");
}


















