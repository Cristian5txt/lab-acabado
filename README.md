#include <iostream>

using namespace std;

void IngresarCristian(float &agua, float &chocolates, float &chicles);
void mostrarCristian(float &agua, float &chocolates, float &chicles, const float &preciO1, const float &preciO2, const float &preciO3);
void comprarCristian(float &agua, float &chocolates, float &chicles, const float &preciO1, const float &preciO2, const float &preciO3, float &dinero, float &saldoTotal);
void mostrarSaldoTotal(float saldoTotal);

int main() {
    float agua, chocolates, chicles,dinero;
    const float preciO1 = 1.20;
    const float preciO2 = 0.65;
    const float preciO3 = 0.50;
    int opcion;
    float saldoTotal = 0;

    IngresarCristian(agua, chocolates, chicles);

    do {
        cout << "*** ESCOJA UNA OPCION ****" << endl;
        cout << "1-Mostrar productos" << endl;
        cout << "2-Comprar productos" << endl;
        cout << "3-Saldo de la maquina" << endl;
        cout << "0-Salir" << endl;
        cout << "ESCOJA UNA OPCION: "<<endl;
        cin >> opcion;

        switch (opcion) {
            case 1:
                mostrarCristian(agua, chocolates, chicles, preciO1, preciO2, preciO3);
                break;
            case 2:
                cout << "INGRESE SU MONEDA: $"<<endl;
                cin >> dinero;
                comprarCristian(agua, chocolates, chicles, preciO1, preciO2, preciO3, dinero, saldoTotal);
                break;
            case 3:
                mostrarSaldoTotal(saldoTotal);
                break;
            case 0:
                cout << "Gracias por comprar" << endl;
                break;
        }
    } while (opcion != 0);

    return 0;
}


void IngresarCristian(float &agua, float &chocolates, float &chicles) {
    cout << "INGRESE LA CANTIDAD DE AGUAS QUE HAY: "<<endl;
    cin >> agua;
    cout << "INGRESE LA CANTIDAD DE CHOCOLATES QUE HAY: "<<endl;
    cin >> chocolates;
    cout << "INGRESE LA CANTIDAD DE CHICLES QUE HAY: "<<endl;
    cin >> chicles;
}


void mostrarCristian(float &agua, float &chocolates, float &chicles, const float &preciO1, const float &preciO2, const float &preciO3) {
    cout << "______________________________" << endl;
    cout << "|CANTIDAD |" << " PRODUCTO |" << " PRECIO |" << endl;
    cout << "|-----------------------------|" << endl;
    cout << "|   " << agua << "    |" << "   AGUAS  |" << "  $" << preciO1 << "  |" << endl;
    cout << "|-----------------------------|" << endl;
    cout << "|   " << chocolates << "    |" << "Chocolates|" << " $" << preciO2 << "  |" << endl;
    cout << "|-----------------------------|" << endl;
    cout << "|   " << chicles << "    |" << " Chicles  |" << " $" << preciO3 << "   |" << endl;
    cout << "------------------------------" << endl;
}

void comprarCristian(float &agua, float &chocolates, float &chicles, const float &preciO1, const float &preciO2, const float &preciO3, float &dinero, float &saldoTotal) {
    int opcionProducto;
    cout << "**** PRODUCTOS DISPONIBLES ****" << endl;
    cout << "1. Agua [$" << preciO1 << "]" << endl;
    cout << "2. Chocolates [$" << preciO2 << "]" << endl;
    cout << "3. Chicles [$" << preciO3 << "]" << endl;
    cout << "ESCOJE EL PRODUCTO QUE GUSTES: "<<endl;
    cin >> opcionProducto;

    switch (opcionProducto) {
        case 1:
            if (agua > 0 && dinero >= preciO1) {
                agua--;
                dinero =dinero-preciO1;
                saldoTotal =saldoTotal+preciO1;
                cout << "Has comprado un Agua tu dinero sobrante: $" << dinero << endl;
            } else if (agua <= 0) {
                cout << "No hay Agua disponible" << endl;
            } else {
                cout << "NO LE ALCANZA" << endl;
            }
            break;
        case 2:
            if (chocolates>0 && dinero >= preciO2) {
                chocolates--;
                dinero =dinero-preciO2;
                saldoTotal =saldoTotal+preciO2;
                cout << "Has comprado un Chocolate tu dinero sobrante: $" << dinero << endl;
            } else if (chocolates <= 0) {
                cout << "No hay Chocolates disponibles" << endl;
            } else {
                cout << "NO LE ALCANZA" << endl;
            }
            break;
        case 3:
            if (chicles > 0 && dinero >= preciO3) {
                chicles--;
                dinero =dinero-preciO3;
                saldoTotal =saldoTotal+preciO3;
                cout << "Has comprado un Chicle tu dinero sobrante es: $" << dinero << endl;
            }
            else if (chicles <= 0) {
                cout << "No hay Chicles disponibles" << endl;
            } else {
                cout << "NO LE ALCANZA" << endl;
            }
            break;
    }
}

void mostrarSaldoTotal(float saldoTotal) {
    cout << "EL VALOR TOTAL ES: $" << saldoTotal << endl;
}
