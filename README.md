# Angular

////////////////////////////////////////
Css.
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  
 
  .form-register {
    width: 400px;
    background: #476786;
    padding: 30px;
    margin: auto;
    margin-top: 100px;
    border-radius: 4px;
    font-family: 'calibri';
    color: white;
   
  }
  
  .form-register h2 {
    font-size: 24px;
    margin-bottom: 20px;

  }
  
  .inputs {
    width: 100%;
    background: #24303c;
    padding: 10px;
    border-radius: 4px;
    margin-bottom: 16px;
    border: 1px solid #476786;
    font-family: 'calibri';
    font-size: 18px;
    color: white;
  }


  .form-register label {
    width: 100%;
    background: #476786;
    padding: 10px;
    font-family: 'calibri';
    font-size: 18px;
    color: rgb(19, 13, 13);
  }
  
  .form-register button {
    width: 100%;
    /* background: #1f53c5; */
    border: #24303c;
    padding: 12px;
    color: #24303c;;
    margin: 16px 0;
    font-size: 16px;
  }

  .cajaSpan{

    width: 400px;
    background: #24303c;
    padding: auto;
    margin: auto;
    margin-top: 100px;
    border-radius: 4px;
    font-family: 'calibri';
    color: white;
  }

  ///////////////////////////////////////////////////////////
  Archivo.html

<p>formulario works!</p>
<!-- registro.component.html -->
<section class="form-register">
    <form #registroForm="ngForm">
        <h2> Formulario de registro </h2>
        <div class="form-group">
            <label for="nombre">Nombre:</label>
            <input class="inputs" type="text" id="nombre" name="nombre" required [(ngModel)]="nombre"
                placeholder="Nombre">
        </div>

        <div class="form-group">
            <label for="correo">Corre electrónico:</label>
            <input class="inputs" type="email" id="correo" name="correo" required [(ngModel)]="correo"
                placeholder="Corre electrónico">
        </div>

        <div class="form-group">
            <label for="direccion">Dirección:</label>
            <input class="inputs" type="text" id="direccion" name="direccion" required [(ngModel)]="direccion"
                placeholder="Dirección">
        </div>

        <div class="form-group">
            <label for="pais">País:</label>
            <!-- <select class="inputs" id="pais" name="pais" required [(ngModel)]="pais"> -->
            <select class="inputs" id="pais" name="pais" required [(ngModel)]="pais">
                <option *ngFor="let pais of paises" [value]="pais.id">{{ pais.nombre }}</option>
            
            </select>
        </div>

        <div class="form-group">
            <label for="estado">Estado:</label>
            <select class="inputs" id="estado" name="estado" required [(ngModel)]="estado">
                <option *ngFor="let estados of estadosPorPais[pais]" [value]="estados">{{ estados }}</option>
            </select>
        </div>

        <button [disabled]="registroForm.invalid" (click)="onSubmit()">Registrar</button>
    </form>
</section>
<section class="cajaSpan">   
    <span *ngIf="nombre"> {{nombre}} - {{correo}} - {{direccion}} - {{pais}} - {{estado}} </span>
</section>

/////////////////////////////////////////////////////////////////////////////
Archivo.Ts


  // registro = {
  //   nombre: '',
  //   apellido: '',
  //   pais: '',
  //   estado: ''
  // };
  nombre: string = "";
  correo: string = "";
  direccion: string = "";
  pais: string = "";
  estado: string = "";

  paises = [
    { id: '1', nombre: 'México'},
    { id: '2', nombre: 'Estados Unidos' },
    { id: '3', nombre: 'Canadá'},
    // Agrega más países y estados según sea necesario
  ];

  estadosPorPais: { [key: string]: string[] } = {
    '1': ['Aguascalientes', 'Baja California', 'Baja California Sur', 'Campeche', 'Chiapas', 'Chihuahua', 'Ciudad de México', 'Coahuila', 'Colima',
      'Durango', 'Estado de México', 'Guanajuato', 'Guerrero', 'Hidalgo', 'Jalisco', 'Michoacán', 'Morelos', 'Nayarit', 'Nuevo León', 'Oaxaca',
      'Puebla', 'Querétaro', 'Quintana Roo', 'San Luis Potosí', 'Sinaloa', 'Sonora', 'Tabasco', 'Tamaulipas', 'Tlaxcala', 'Veracruz', 'Yucatán', 'Zacatecas'
    ],
    '2': ['Alabama', 'Alaska', 'Arizona', 'Arkansas', 'California', 'Colorado', 'Connecticut', 'Delaware', 'Florida', 'Georgia', 'Hawaii', 'Idaho',
      'Illinois', 'Indiana', 'Iowa', 'Kansas', 'Kentucky', 'Louisiana', 'Maine', 'Maryland', 'Massachusetts', 'Michigan', 'Minnesota', 'Mississippi',
      'Missouri', 'Montana', 'Nebraska', 'Nevada', 'New Hampshire', 'New Jersey', 'New Mexico', 'New York', 'Carolina del Norte', 'Dakota del Norte',
      'Ohio', 'Oklahoma', 'Oregon', 'Pennsylvania', 'Rhode Island', 'Carolina del Sur', 'Dakota del Sur', 'Tennessee', 'Texas', 'Utah', 'Vermont',
      'Virginia', 'Washington', 'Virginia', 'Wisconsin'
    ],
    '3': ['Alberta', 'Columbia Británica', 'Manitoba', 'Nuevo Brunswick', 'Terranova y Labrador', 'Nueva Escocia', 'Ontario', 'Isla del Príncipe Eduardo',
      'Quebec', 'Saskatchewan', 'Yukon', 'Nunavut', 'Territorios del Noroeste'
    ]
  };

  onSubmit() {
    
      // Mostar datos en consola
      console.log('Datos del formulario:', this.nombre, this.correo, this.direccion, this.pais, this.estado);

      // Redirigir al usuario a una página de inicio de sesión o de agradecimiento
      // this.router.navigate(['/inicio-sesion']); // Asegúrate de importar RouterModule y ActivatedRoute para utilizar esta opción
    }
