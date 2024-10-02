<template>
  
  <div>
    <select v-model="selectedProvince" @change="fetchCities">
      <option v-for="province in provinces" :key="province">
        {{ province }}
      </option>
    </select>

    <select v-model="selectedCity" @change="fetchBarangays" :disabled="!selectedProvince">
      <option v-for="city in cities" :key="city">
        {{ city }}
      </option>
    </select>

    <select v-model="selectedBarangay" :disabled="!selectedCity">
      <option v-for="barangay in barangays" :key="barangay">
        {{ barangay }}
      </option>
    </select>
  </div>


  <div>
    <input type="checkbox" class="checkbox"> 
  </div>
</template>

<script>
export default {
  data() {
    return {
      provinces: [
    "Abra",
    "Agusan del Norte", 
    "Agusan del Sur", 
    "Aklan",
    "Albay", 
    "Antique",
    "Apayao",
    "Aurora",
    "Basilan",
    "Bataan",
    "Batanes",
    "Batangas",
    "Benguet",
    "Biliran",
    "Bohol",
    "Bukidnon",
    "Bulacan",
    "Cagayan",
    "Camarines Norte",
    "Camarines Sur",
    "Camiguin",
    "Capiz",
    "Catanduanes",
    "Cavite",
    "Cebu",
    "Cotabato",
    "Davao de Oro (Compostela Valley)",
    "Davao del Norte",
    "Davao del Sur",
    "Davao Occidental",
    "Davao Oriental",
    "Dinagat Islands",
    "Eastern Samar",
    "Guimaras",
    "Ifugao",
    "Ilocos Norte",
    "Ilocos Sur",
    "Iloilo",
    "Isabela",
    "Kalinga",
    "La Union",
    "Laguna",
    "Lanao del Norte",
    "Lanao del Sur",
    "Leyte",
    "Maguindanao del Norte",
    "Maguindanao del Sur",
    "Marinduque",
    "Masbate",
    "Misamis Occidental",
    "Misamis Oriental",
    "Mountain Province",
    "Negros Occidental",
    "Negros Oriental",
    "Northern Samar",
    "Nueva Ecija",
    "Nueva Vizcaya",
    "Occidental Mindoro",
    "Oriental Mindoro",
    "Palawan",
    "Pampanga",
    "Pangasinan",
    "Quezon",
    "Quirino",
    "Rizal",
    "Romblon",
    "Samar",
    "Sarangani",
    "Siquijor",
    "Sorsogon",
    "South Cotabato",
    "Southern Leyte",
    "Sultan Kudarat",
    "Sulu",
    "Surigao del Norte",
    "Surigao del Sur",
    "Tarlac",
    "Tawi-Tawi",
    "Zambales",
    "Zamboanga del Norte",
    "Zamboanga del Sur",
    "Zamboanga Sibugay"//finished
],

      cities: [],
      barangays: [],
      selectedProvince: null,
      selectedCity: null,
      selectedBarangay: null,
    };
  },
  created() {
   
    this.citiesByProvince = {
      "Abra": [
  "Bangued",
  "Bacnotan",
  "Boliney",
  "Bucay",
  "Bucloc",
  "Daguioman",
  "Danglas",
  "Dolores",
  "La Paz",
  "Lacub",
  "Lagangilang",
  "Lagayan",
  "Langiden",
  "Licuan-Baay",
  "Luba",
  "Malibcong",
  "Manabo",
  "Peñarrubia",
  "Pidigan",
  "Pilar",
  "Sallapadan",
  "San Isidro",
  "San Juan",
  "San Quintin",
  "Tayum",
  "Tineg",
  "Tubo",
  "Villaviciosa"
],

"Agusan del Norte": [
  "Butuan",
  "Cabadbaran",
  "Carmen",
  "Jabonga",
  "Kitcharao",
  "Las Nieves",
  "Magallanes",
  "Nasipit",
  "Remedios T. Romualdez",
  "Santiago",
  "Tubay"
],

"Agusan del Sur": [
  "Bayugan",
  "Esperanza",
  "Prosperidad",
  "San Luis",
  "Sibagat",
  "Talacogon"
],

"Aklan": [
  "Kalibo",
  "Balete",
  "Banga",
  "Batan",
  "Buruanga",
  "Ibajay",
  "Lezo",
  "Libacao",
  "Madalag",
  "Makato",
  "Malay",
  "Malinao",
  "Nabas",
  "New Washington",
  "Numancia",
  "Tangalan"
],

"Albay": [
  "Legazpi",
  "Ligao",
  "Tabaco",
  "Camalig",
  "Daraga",
  "Guinobatan",
  "Jovellar",
  "Libon",
  "Malilipot",
  "Malinao",
  "Manito",
  "Oas",
  "Pio Duran",
  "Polangui",
  "Rapu-Rapu",
  "Santo Domingo",
  "Tiwi"
],

"Antique": [
  "Anini-y",
  "Barbaza",
  "Belison",
  "Bugasong",
  "Caluya",
  "Culasi",
  "Hamtic",
  "Laua-an",
  "Libertad",
  "Pandan",
  "Patnongon",
  "San Jose de Buenavista", 
  "San Remigio",
  "Sebaste",
  "Sibalom",
  "Tibiao",
  "Tobias Fornier",
  "Valderrama"
],

"Apayao": [
  "Calanasan",
  "Conner",
  "Flora",
  "Kabugao",
  "Luna",
  "Pudtol",
  "Santa Marcela"
],

"Aurora": [
  "Baler",
  "Casiguran",
  "Dilasag",
  "Dinalungan",
  "Dingalan",
  "Dipaculao",
  "Maria Aurora",
  "San Luis"
],

"Basilan": [
  "Isabela",
  "Lamitan",
  "Al-Barka",
  "Hadji Mohammad Ajul",
  "Hadji Muhtamad",
  "Lantawan",
  "Maluso",
  "Sumisip",
  "Tabuan-Lasa",
  "Tipo-Tipo",
  "Tuburan",
  "Ungkaya Pukan"
],
"Bataan": [
  "Balanga"
],
"Batanes": [
  "Basco",
  "Itbayat",
  "Ivana",
  "Mahatao",
  "Sabtang",
  "Uyugan"
],
"Batangas": [
  "Batangas City",
  "Lipa City",
  "Tanauan City",
  "Santo Tomas City",
  "Calaca",
  "Laurel",
  "San Juan",
  "San Luis",
  "San Nicolas",
  "San Pascual",
  "Santa Teresita",
  "Taal",
  "Talisay",
  "Taysan",
  "Tingloy"
],
"Benguet": [
  "Baguio",
  "Atok",
  "Bakun",
  "Bokod",
  "Buguias",
  "Itogon",
  "Kabayan",
  "Kapangan",
  "Kibungan",
  "La Trinidad",
  "Mankayan",
  "Sablan",
  "Tuba",
  "Tublay"
],
"Biliran": [
  "Almeria",
  "Biliran",
  "Cabucgayan",
  "Caibiran",
  "Culaba",
  "Kawayan",
  "Maripipi",
  "Naval"
],
"Bohol": [
  "Tagbilaran City",
  "Alburquerque",
  "Baclayon",
  "Balilihan",
  "Batuan",
  "Bien Unido",
  "Bilar",
  "Buenavista",
  "Calape",
  "Candijay",
  "Carmen",
  "Dauis",
  "Dimiao",
  "Garcia Hernandez",
  "Jagna",
  "Loboc",
  "Loon",
  "Mabini",
  "Panglao",
  "Sangkat",
  "San Isidro",
  "San Miguel",
  "Sevilla",
  "Sierra Bullones",
  "Sikatuna",
  "Sogod",
  "Talibon",
  "Trinidad",
  "Tubigon",
  "Ubay",
  "Valencia"
],
"Bukidnon": [
  "Malaybalay",
  "Impasugong",
  "Valencia",
  "Cabanglasan",
  "San Fernando",
  "Maramag",
  "Quezon",
  "Don Carlos",
  "Kitaotao",
  "Dangcagan",
  "Kibawe",
  "Damulog",
  "Baungon",
  "Libona",
  "Malitbog",
  "Manolo Fortich",
  "Sumilao",
  "Talakag"
],
"Bulacan": [
  "Malolos",
  "Baliwag",
  "Meycauayan",
  "San Jose del Monte",
  "Angat",
  "Balagtas",
  "Bocaue",
  "Bustos",
  "Calumpit",
  "Doña Remedios Trinidad",
  "Guiguinto",
  "Hagonoy",
  "Marilao",
  "Norzagaray",
  "Obando",
  "Pandi",
  "Paombong",
  "Plaridel",
  "Pulilan",
  "San Ildefonso",
  "San Miguel",
  "San Rafael",
  "Santa Maria"
],
"Cagayan": [
  "Tuguegarao",
  "Alcala",
  "Allacapan",
  "Amulung",
  "Aparri",
  "Baggao",
  "Ballesteros",
  "Buguey",
  "Calayan",
  "Camalaniugan",
  "Claveria",
  "Enrile",
  "Gattaran",
  "Gonzaga",
  "Iguig",
  "Lal-lo",
  "Lasam",
  "Pamplona",
  "Peñablanca",
  "Piat",
  "Rizal",
  "Sanchez-Mira",
  "Santa Ana",
  "Santa Praxedes",
  "Santa Teresita",
  "Santo Niño",
  "Solana",
  "Tuao"
],
"Camarines Norte": [
  "Basud",
  "Daet",
  "Jose Panganiban",
  "Labo",
  "Mercedes",
  "Paracale",
  "San Lorenzo Ruiz",
  "San Vicente",
  "Santa Elena",
  "Talisay",
  "Vinzons"
],
"Camarines Sur": [
  "Cabusao",
  "Calabanga",
  "Camaligan",
  "Canaman",
  "Caramoan",
  "Del Gallego",
  "Garchitorena",
  "Goa",
  "Lagonoy",
  "Libmanan",
  "Lupi",
  "Magarao",
  "Milaor",
  "Minalabac",
  "Nabua",
  "Ocampo",
  "Pamplona",
  "Pasacao",
  "Pili",
  "Presentacion",
  "Ragay",
  "Sagñay",
  "San Fernando",
  "San Jose",
  "Sipocot",
  "Siruma",
  "Tigaon",
  "Tinambac"
],
"Camiguin": [
  "Mambajao",
  "Catarman",
  "Guinsiliban",
  "Mahinog",
  "Sagay"
],
"Capiz": [
  "Roxas City",
  "Aklan",
  "Altavas",
  "Balete",
  "Banga",
  "Batan",
  "Caluya",
  "Cuartero",
  "Dao",
  "Dulong",
  "Dumalag",
  "Dumarao",
  "Ivisan",
  "Jamindan",
  "Maayon",
  "Mambusao",
  "Panay",
  "Panitan",
  "Pilar",
  "Pontevedra",
  "President Roxas",
  "Sapian",
  "Sigma",
  "Tapaz"
],
"Catanduanes": [
  "Virac",
  "Bagamanoc",
  "Baras",
  "Bato",
  "Caramoran",
  "Gigmoto",
  "Pandan",
  "Panganiban",
  "San Andres",
  "San Miguel",
  "Viga"
],
"Cavite": [
  // First District
  "Cavite City",
  "Kawit",
  "Noveleta",
  "Rosario",

  // Second District
  "Bacoor",

  // Third District
  "Imus",

  // Fourth District
  "Dasmariñas City",

  // Fifth District
  "Carmona",
  "Silang",

  // Sixth District
  "Trece Martires City",
  "General Trias",

  // Seventh District
  "Tagaytay City",
  "Alfonso",
  "Indang",
  "General Emilio Aguinaldo",
  "Magallanes",
  "Maragondon",
  "Mendez",
  "Naic",
  "Ternate",
],

"Cebu": [
  "Cebu City",
  "Aguadilla",
  "Alcantara",
  "Alegria",
  "Alcoy",
  "Aloguinsan",
  "Argao",
  "Asturias",
  "Badian",
  "Balamban",
  "Bantayan",
  "Barili",
  "Bogo City",
  "Boljoon",
  "Carmen",
  "Catmon",
  "Compostela",
  "Consolacion",
  "Cordova",
  "Danao City",
  "Daanbantayan",
  "Delgado",
  "Dumanjug",
  "Ginatilan",
  "Guardia",
  "Guiwanon",
  "Lawaan",
  "Liloan",
  "Madridejos",
  "Malabuyoc",
  "Mandaue City",
  "Medellin",
  "Minglanilla",
  "Moalboal",
  "Oslob",
  "San Fernando",
  "San Francisco",
  "San Remigio",
  "Santa Fe",
  "Santander",
  "Sibonga",
  "Sogod",
  "Toledo City",
  "Tudela",
  "Tuburan",
],

"Cotabato": [
  "Alamada",
  "Aleosan",
  "Banisilan",
  "Baribas",
  "Buluan",
  "Cotabato City",
  "Datu Odin Sinsuat",
  "Gen. Santos City",
  "Kabacan",
  "Kidapawan",
  "Libungan",
  "M'lang",
  "Magpet",
  "Matanog",
  "Norala",
  "Pagalungan",
  "Parang",
  "Pikit",
  "Pigcawayan",
  "Polopina",
  "President Roxas",
  "Rajah Buayan",
  "Shariff Aguak",
  "Shariff Saydona Mustafa",
  "Surallah",
  "Tampakan",
  "Tamparan",
  "Tulunan",
],
"Davao de Oro (Compostela Valley)": [
  "Compostela",
  "Laak",
  "Mabini",
  "Maco",
  "Maragusan",
  "Mawab",
  "Monkayo",
  "Montevista",
  "Nabunturan",
  "New Bataan",
  "Pantukan",
],
"Davao del Norte": [
  "Tagum", // Provincial capital and highly urbanized city
  "Panabo", // Highly urbanized city and industrial center
  "Samal", // Island city known for its beaches and resorts
  "Island Garden City of Samal", // Alternative name for Samal City
  "Carmen", // Town known for its agricultural lands and scenic views
  "Kapalong", // Town known for its indigenous culture and waterfalls
  "Maco", // Town known for its historical landmarks and hot springs
  "Monkayo", // Town known for its pineapple plantations and waterfalls
  "Nabunturan", // Town known for its fruit orchards and Durian Festival
  "New Corella", // Town known for its rice terraces and pineapple farms
  "San Isidro", // Town known for its agricultural lands and waterfalls
  "Santo Tomas", // Town known for its caves and hot springs
  "Talaingod", // Town known for its indigenous culture and Mount Apo
],
"Davao del Sur": [
  "Digos City", // Independent city and former provincial capital
  "Bansalan", // Known for its fruit plantations and waterfalls
  "Don Marcelino", // Rich in agricultural resources and scenic landscapes
  "Hagonoy", // Home to the Davao Crocodile Park and hot springs
  "Jose Abad Santos", // Gateway to Mount Apo, the highest peak in the Philippines
  "Kiblawan", // Town known for its rice terraces and indigenous culture
  "Magsaysay", // Rich in agricultural lands and a gateway to Mount Apo
  "Malalag", // Provincial capital and known for its pineapple farms
  "Malita", // Previously part of Davao del Sur, now the capital of Davao Occidental
  "Matanao", // Town known for its durian plantations and waterfalls
  "Padada", // Scenic town with beaches and coastal attractions
  "Santa Cruz", // Known for its historical landmarks and pineapple farms
  "Santa Maria", // Previously part of Davao del Sur, now part of Davao Occidental
  "Sarangani", // Previously part of Davao del Sur, now the capital of Sarangani
  "Sulop", // Town known for its rice terraces and historical sites
],
"Davao Occidental": [
  "Don Marcelino", // Third Class Municipality
  "Jose Abad Santos", // First Class Municipality
  "Malita", // First Class Municipality
  "Santa Maria (DS)", // Second Class Municipality
  "Sarangani", // Fourth Class Municipality
],
"Davao Oriental": [
  "Mati", // Provincial capital and major commercial center //imy matti
  "Banaybanay", // Town known for its natural beauty and agricultural lands
  "Boston", // Town known for its hot springs and waterfalls
  "Caraga", // Town known for its rich history and coastal location
  "Cateel", // Town known for its pristine beaches and marine life
  "Governor Generoso", // Town known for its agricultural produce and pineapple farms
  "Lupon", // Town known for its waterfalls and rice terraces
  "Manay", // Town known for its hot springs and agricultural farms
  "San Isidro", // Town known for its scenic mountains and diverse plants
  "Tarragona", // Town known for its rich historical sites and cultural heritage
],
"Dinagat Islands": [
  "Basilisa", // Municipality known for its natural beauty and agricultural lands
  "Cagdianao", // Municipality with significant mineral resources and diverse marine life
  "Dinagat", // Provincial capital and historical town with old churches
  "Libjo", // Municipality known for its mangroves and fish sanctuaries
  "Loreto", // Municipality with scenic landscapes and abundant agricultural products
  "San Jose", // Largest municipality with growing urbanization and economic development
  "Tubajon", // Island municipality known for its pristine beaches and marine biodiversity
],
"Eastern Samar": [
        "Allen",
        "Balangiga",
        "Balangkayan",
        "Borongan", // Provincial capital
        "Can-avid",
        "Catbalogan",
        "Hernani",
        "Giporlos",
        "Guiuan",
        "Lawaan",
        "Llorente",
        "Maydolong",
        "Mercedes",
        "Oras",
        "Salcedo",
        "Taft",
        "Tulunggan",
      ],
      "Guimaras": [
  "Buena Vista", // Provincial capital and home to Barasol Eco Farm
  "Jordan", // Gateway to Guimaras and known for its mangrove forests
  "Nueva Valencia", // Home to the Manggahan Festival and Guimaras Island Wildlife Sanctuary
  "San Lorenzo", // Scenic town with beautiful beaches and resorts
  "Sibunag", // Town known for its historical landmarks and agricultural lands
],
"Ifugao": [
  // No cities exist in Ifugao, only municipalities.
  "Kiangan", // Municipal district known for its rice terraces and historical sites
  "Banaue", // Municipal district famous for the Batad Rice Terraces
  "Mayoyao", // Municipal district known for its indigenous culture and rice terraces
  "Lamut", // Municipal district with scenic landscapes and rice terraces
  "Hungduan", // Municipal district popular for its waterfalls and caves
  "Alfonso Lista", // Municipal district known for its rice terraces and indigenous crafts
  "Aguinaldo", // Municipal district featuring the Ampuñgan Rice Terraces
  "Hingyon", // Municipal district with rich natural resources and rice terraces
  "Tinoc", // Municipal district known for its traditional villages and rice terraces
],
"Ilocos Norte": [
  "Adams",
  "Bacarra", // Historical town with cobblestone streets and Spanish colonial architecture
  "Badoc", // Town known for its rice terraces and scenic landscapes
  "Bangui", // Home to the Sand Dunes Adventure Park
  "Banna", // Gateway to Paoay Lake and the Kapurpurawan Rock Formations
  "Burgos", // Town known for its traditional weaving industry and pottery
  "Carasi", // Scenic town with mountains, caves, and waterfalls
  "Currimao", // Gateway to Saud Beach and the Malacanang sa Norte Palace
  "Dingras", // Home to the Pindangan Ruins and the Dingras Wind Farm
  "Dumalneg", // Town known for its rice terraces and indigenous culture
  "Laoag City", // Provincial capital and center of business and commerce
  "Marcos", // Town known for its historical landmarks and scenic beauty
  "Nueva Era", // Home to the Nueva Era Sand Dunes and the Nagpuan Point Lighthouse
  "Pagudpud", // Popular tourist destination with white sand beaches and surfing spots
  "Paoay", // UNESCO World Heritage Town known for its centuries-old churches and bell towers
  "Pasuquin", // Town known for its historical churches and pottery craft
  "Piddig", // Gateway to the Kabuhatang National Park and the Sand Dunes of La Paz
  "Pinili", // Town known for its white sand beaches and coral reefs
  "San Nicolas", // Home to the Sand Dunes of Bacsil and the Pinzal Cave
  "Sarrat", // Town known for its historical landmarks and traditional dance festivals
  "Solsona", // Gateway to the Magsingal River and the Maligcong Bridge
  "Vintar", // Historical town with Spanish colonial architecture and rice terraces
],
"Ilocos Sur": [
  "Vigan", // Provincial capital and UNESCO World Heritage City
  "Bantay", // Scenic town known for its bell tower and heritage structures
  "Caoayan", // Town known for its historical landmarks and traditional weaving
  "Candon", // Largest city in Ilocos Sur with historical churches and museums
  "Currimao", // Town known for its beaches and surfing spots
  "Dingras", // Historical town known for its tobacco industry and ancestral homes
  "Estancia", // Coastal town known for its seafood and scenic views
  "Galimuyod", // Mountainous town with waterfalls and caves
  "La Paz", // Town known for its hot springs and rice terraces
  "Narvacan", // Town known for its historical landmarks and traditional crafts
  "Nagbukel", // Town known for its rice terraces and scenic landscapes
  "Santa", // Town known for its historical churches and cultural heritage
  "Santa Catalina", // Coastal town known for its sand dunes and windsurfing
  "Santa Cruz", // Town known for its beaches and diving spots
  "Santa Maria", // Town known for its historical church and ancestral homes
  "San Esteban", // Town known for its rice terraces and hot springs
  "San Juan", // Town known for its historical landmarks and traditional weaving
  "San Vicente", // Town known for its beaches and scenic views
  "Sinait", // Town known for its historical landmarks and pottery industry
  "Vintar", // Coastal town known for its seafood and sand dunes
],
"Iloilo": [
  "Iloilo City", // Provincial capital and highly urbanized city
  "Ajuy", // Town known for its seafood and sand dunes
  "Alimodian", // Home to the Hinugyaw Festival and Hidden Valley Springs
  "Antique", // Scenic town with agricultural lands and waterfalls
  "Banate", // Gateway to Guimaras Island and its mango farms
  "Barotac Nuevo", // Town known for its historical landmarks and beaches
  "Barotac Viejo", // Historical town with Spanish colonial architecture
  "Batad", // Home to the Binalaybay Festival and rice terraces
  "Bingawan", // Gateway to the Iloilo River and historical churches
  "Cabatuan", // Scenic town with mountains and hot springs
  "Carles", // Home to the Pintados de Pasion Festival and beaches
  "Concepcion", // Town known for its historical landmarks and religious sites
  "Dingle", // Gateway to the Iloilo-Guimaras Strait and mangrove forests
  "Dumaguete", // Scenic town with mountains and waterfalls
  "Dumangas", // Home to the Pasunday Festival and vibrant culture
  "Estancia", // Town known for its sugarcane plantations and beaches
  "Guimbal", // Historical town with Spanish colonial architecture
  "Igbaras", // Gateway to Mount Madia-as and its breathtaking views
  "Janiuay", // Home to the Tinubu Festival and hot springs
  "Jordan", // Town known for its fruit orchards and agricultural landscapes
  "Kalibo", // Town with unique rock formations and scenic rivers
  "Leon", // Historical town with Spanish colonial churches and ruins
  "Leganes", // Gateway to the Iloilo River and mangrove forests
  "Lopez", // Town known for its rice terraces and mountain landscapes
  "Maasin", // Scenic town with waterfalls and hidden coves
  "Miag-ao", // Home to the UNESCO World Heritage Site Miag-ao Church
  "Mina", // Town known for its hot springs and agricultural lands
  "New Lucena", // Gateway to Panay River and its diverse wildlife
  "Oton", // Town known for its historical landmarks and beaches
  "Passi", // Home to the Passi City Tuna Festival and vibrant culture
  "San Enrique", // Town known for its sugarcane plantations and rice terraces
  "San Joaquin", // Gateway to Iloilo River and its rich biodiversity
  "Santa Barbara", // Town known for its traditional crafts and heritage
  "Sara", // Scenic town with mountains and waterfalls
  "Sebaste", // Home to the Tinubuan Festival and agricultural landscapes
  "Sipi", // Town known for its beaches and marine sanctuaries
  "Sta. Barbara", // Scenic town with mountains and hot springs
  "Tiaong", // Town with historical landmarks and religious sites
  "Tubungan", // Gateway to Mount Cabuyao and its breathtaking views
  "Zarraga", // Town known for its rice terraces and indigenous culture
],
"Isabela": [
  "Cauayan City", // City known for its Magat Dam and San Mateo River Cruise
  "Ilagan City", // Provincial capital and historical center
  "Santiago City", // Gateway to the Cagayan Valley
  "Alicia", // Town known for its rice terraces and scenic views
  "Angadanan", // Historical town with Spanish colonial architecture
  "Aurora", // Home to the Aurora Park and wildlife sanctuary
  "Benito Soliven", // Town known for its caves and waterfalls
  "Burgos", // Gateway to the Sierra Madre Mountains
  "Cabagan", // Town known for its hot springs and agricultural lands
  "Cordon", // Home to the Cabuyao Falls and rice terraces
  "Delfin Albano", // Town known for its historical landmarks and festivals
  "Dinapigue", // Scenic town with a rich indigenous culture
  "Divilacan", // Gateway to the Magat River and eco-tourism activities
  "Echague", // Town known for its Spanish colonial churches and heritage
  "Gamu", // Home to the Magat Dam and hydroelectric power plant
  "Jones", // Scenic town with panoramic views and rice terraces
  "Luna", // Town known for its agricultural lands and scenic landscapes
  "Maconacon", // Home to the Pinzal Falls and eco-tourism activities
  "Mallig", // Gateway to the Mallig Plains and agricultural lands
  "Naguilian", // Town known for its hot springs and waterfalls
  "Palanan", // Island municipality known for its pristine beaches and coral reefs
  "Quezon", // Home to the Dupax del Norte Wildlife Sanctuary
  "Quirino", // Town known for its historical landmarks and agricultural lands
  "Ramon", // Gateway to the Sierra Madre Mountains and caves
  "Reina Mercedes", // Town known for its waterfalls and hot springs
  "Roxas", // Home to the Roxas Dam and Magat River resorts
  "San Agustin", // Town known for its historical churches and festivals
  "San Guillermo", // Scenic town with rice terraces and mountain views
  "San Isidro", // Gateway to the Cagayan Valley and agricultural lands
  "San Manuel", // Home to the Pinzal Falls and eco-tourism activities
  "San Mariano", // Town known for its hot springs and historical landmarks
  "San Mateo", // Home to the Magat Dam and river cruises
  "Santa Maria", // Town known for its rice terraces and agricultural lands
  "Santo Tomas", // Gateway to the Magat River and eco-tourism activities
  "Tumauini", // Historical town with Spanish colonial architecture
],
"Kalinga": [
  "Tabuk", // Provincial capital and component city
  "Balbalan", // Third class municipality
  "Lubuagan", // Fourth class municipality
  "Pasil", // Fifth class municipality
  "Pinukpuk", // First class municipality
  "Rizal", // Fourth class municipality
  "Tanudan", // Fourth class municipality
  "Tinglayan", // Fourth class municipality
],
"La Union": [
  "Agoo", // Historical town with the Basilica Minore del Santo Niño
  "Aringay", // Scenic coastal town with surfing spots
  "Bacnotan", // Town known for its Spanish colonial architecture and beaches
  "Bagulin", // Mountainous town with rice terraces and agricultural lands
  "Balaoan", // Gateway to La Union Botanical Garden and Bauang Beach
  "Bangar", // Coastal town with historic churches and sand dunes
  "Bauang", // Popular tourist destination with beaches and grape farms
  "Burgos", // Town known for its rice terraces and hot springs
  "Caba", // Gateway to Tangadan Falls and Tangadan Falls Natural Park
  "Luna", // Scenic town with diverse landscapes and rice terraces
  "Naguilian", // Gateway to Bauang Beach and Camp Luna
  "Pugo", // Town known for its historical landmarks and traditional crafts
  "Rosario", // Gateway to the Ilocos Sur border and agricultural lands
  "San Gabriel", // Town known for its historical churches and traditional art
  "San Juan", // Surfing capital of the North with popular beaches
  "Santo Tomas", // Town known for its beaches and sand dunes
  "Santol", // Coastal town with agricultural lands and fishponds
  "Sudipen", // Town known for its rice terraces and mountain views
  "Tubao", // Town known for its historical landmarks and traditional weaving
],
"Laguna": [
  // Highly Urbanized Cities
  "Biñan",
  "Calamba",
  "Santa Rosa",
  "Cabuyao",
  // Municipalities
  "Alaminos",
  "Bay",
  "Calauan",
  "Cavinti",
  "Famy",
  "Kalayaan",
  "Liliw",
  "Los Baños",
  "Luisiana",
  "Lumban",
  "Mabitac",
  "Magdalena",
  "Majayjay",
  "Nagcarlan",
  "Paete",
  "Pagsanjan",
  "Pakil",
  "Pangil",
  "Pila",
  "Rizal",
  "Santa Cruz",
  "Santa Maria",
  "Siniloan",
  "Victoria",
],
"Lanao del Norte": [
  "Bacolod",
  "Baloi",
  "Baroy",
  "Kauswagan",
  "Kolambugan",
  "Linamon",
  "Maigo",
  "Matungao",
  "Pantar",
  "Tagoloan",
  "Tubod",
  "Kapatagan",
  "Lala",
  "Magsaysay",
  "Munai",
  "Nunungan",
  "Pantao Ragat",
  "Poona Piagapo",
  "Salvador",
  "Sapad",
  "Sultan Naga Dimaporo",
  "Tangcal",
],
"Lanao del Sur": [
        "Marawi City", // Provincial capital
        "Bacolod-Kalawi", // Town known for its Islamic architecture
        "Balabagan", // Gateway to Lake Lanao
        "Balindong", // Town known for its rice terraces
        "Bayang", // Home to the Maranao Cultural Village
        "Binidayan", // Scenic town with waterfalls and caves
        "Buadiposo-Buntong", // Town known for its hot springs and natural resources
        "Bubong", // Home to the Lanao del Sur Museum
        "Butig", // City known for its pineapple plantations
        "Calanogas", // Town known for its rice terraces and handicrafts
        "Ditsaan-Ramain", // Home to the Ditsaan-Ramain Festival
        "Ganassi", // Town known for its historical landmarks
        "Kapai", // Gateway to Mount Apo
        "Kapatagan", // Town known for its fruit orchards and scenic views
        "Lumba-Bayabao", // Home to the Lumba-Bayabao Festival
        "Lumbaca-Unayan", // Town known for its waterfalls and caves
        "Lumbatan", // Scenic town with a rich cultural heritage
        "Lumbayanague", // Home to the Lumbayanague Festival
        "Madalum", // Town known for its hot springs and rice terraces
        "Madamba", // Gateway to the Madamba River
        "Maging", // Town known for its agricultural lands and scenic views
        "Malabang", // City known for its historical significance
        "Marantao", // Town known for its traditional crafts and festivals
        "Marogong", // City known for its pineapple plantations and scenic views
        "Masiu", // Gateway to Lake Lanao
        "Mulondo", // Town known for its rice terraces and waterfalls
        "Pagayawan", // City known for its rice paddies and agricultural products
        "Piagapo", // Town known for its historical landmarks and festivals
        "Picong", // Home to the Picong Festival
        "Poona Bayabao", // Town known for its waterfalls and rice terraces
        "Pualas", // Scenic town with diverse marine life and coral reefs
        "Saguiaran", // Gateway to Mount Piapayungan
        "Sultan Dumalondong", // Town known for its historical landmarks and Islamic architecture
        "Tagoloan II", // City known for its rice paddies and agricultural products
        "Tamparan", // Town known for its hot springs and rice terraces
        "Taraka", // City known for its pineapple plantations and scenic views
        "Tubaran", // Town known for its waterfalls and caves
        "Tugaya", // Gateway to Lake Butig
        "Wao", // City known for its rice paddies and agricultural products
      ],
      "Leyte": [
  "Tacloban City", // Provincial capital and independent city
  "Alangalang", // Town known for its rice terraces and waterfalls
  "Abuyog", // Gateway to Lake Danao and Mount Cabuyao
  "Babatngon", // Home to the Maligao Festival and historical churches
  "Barugo", // Historical town with Spanish colonial architecture
  "Bato", // Town known for its beaches and diving spots
  "Baybay", // Home to the Tuna Festival and Mahaplag Volcano
  "Burauen", // Gateway to the Leyte Ecological Park and Wildlife Sanctuary
  "Calubian", // Island municipality known for its coral reefs and sandbars
  "Capoocan", // Scenic town with agricultural lands and scenic views
  "Carigara", // Home to the Pintados de Carigara Festival and the San Juanico Bridge
  "Dagami", // Town known for its hot springs and historical landmarks
  "Dulag", // Gateway to the Leyte Gulf and World War II memorials
  "Hilongos", // Town known for its beaches and seafood restaurants
  "Hindang", // Home to the Malunggay Festival and rice terraces
  "Inopacan", // Gateway to the Maasin River and mangrove forests
  "Isabel", // Town known for its waterfalls and natural attractions
  "Jaro", // Home to the Leyte Sabor Festival and historical churches
  "Javier", // Town known for its rice terraces and traditional crafts
  "Julita", // Town known for its hot springs and agricultural lands
  "Kananga", // Home to the Kananga Falls and Bato Caves
  "La Paz", // Town known for its beaches and coconut plantations
  "Leyte", // Town known for its historical landmarks and rice terraces
  "MacArthur", // Gateway to the MacArthur Landing Memorial Park
  "Mahaplag", // Town known for its volcanoes and geothermal power plants
  "Matag-ob", // Town known for its rice terraces and scenic views
  "Matalom", // Gateway to Sogod Bay and mangrove forests
  "Mayorga", // Home to the Mayorgang Litson Festival and historical churches
  "Merida", // Town known for its beaches and agricultural lands
  "Ormoc City", // Independent city known for its historical landmarks and volcanoes
  "Palo", // City known for its historical landmarks and Calbayog Falls
  "Palompon", // Town known for its beaches and seafood restaurants
  "Pastrana", // Town known for its rice terraces and scenic views
  "San Isidro", // Town known for its hot springs and natural attractions
  "San Miguel", // Town known for its beaches and coconut plantations
  "Santa Fe", // Town known for its historical landmarks and rice terraces
  "Tabango", // Town known for its beaches and agricultural lands
  "Tabontabon", // Island municipality known for its coral reefs and sandbars
  "Tanauan", // Town known for its beaches and seafood restaurants
  "Tolosa", // Town known for its historical landmarks and rice terraces
  "Tunga", // Town known for its waterfalls and natural attractions
  "Villaba", // Gateway to the Leyte Sabor Festival and historical churches
],
"Maguindanao del Norte": [
  "Barira",
  "Buldon",
  "Datu Blah T. Sinsuat",
  "Datu Odin Sinsuat",
  "Kabuntalan",
  "Matanog",
  "Northern Kabuntalan",
  "Parang",
  "Sultan Kudarat", // Provincial capital
  "Sultan Mastura",
  "Talitay",
  "Upi",
],
"Maguindanao del Sur": [
      "Ampatuan",
      "Buluan",
      "Datu Abdullah Sangki",
      "Datu Anggal Midtimbang",
      "Datu Hoffer Ampatuan",
      "Datu Montawal",
      "Datu Paglas",
      "Datu Piang",

      
"Datu Salibo",
      "Datu Saudi Ampatuan",
      "Datu Unsay",
      "General Salipada K. Pendatun",
      "Guindulungan",
      "Mamasapano",
      "Mangudadatu",
      "Pagalungan",
      "Paglat",
      "Pandag",
      "Rajah Buayan",
      "Shariff Aguak",
      "Shariff Saydona Mustapha",
      "Sultan sa Barongis",
      "Talayan",
      "South Upi",
    ],
    "Marinduque": [
      "Boac", // Provincial capital and largest municipality
      "Buenavista", // Known for its beautiful beaches and diving sites
      "Gasan", // Home to the Marinduque State College and rice terraces
      "Mogpog", // Gateway to the Tres Marias Islands and Morion Festival
      "Santa Cruz", // Second largest municipality with historical churches
      "Torrijos", // Scenic town known for its caves and waterfalls
    ],
    "Masbate": [
      "Masbate City", // Provincial capital
      "Aroroy", // Town known for its mangrove forests and marine sanctuaries
      "Baleno", // Scenic town with hidden coves and waterfalls
      "Batuan", // Island municipality with pristine beaches and coral reefs
      "Cagayonce", // Town known for its hot springs and historical landmarks
      "Catanauan", // Gateway to Ticao Island and its diverse marine life
      "Claveria", // Town known for its rice terraces and indigenous traditions
      "Dimasalang", // Historical town with Spanish colonial architecture
      "Esperanza", // Town known for its agricultural landscapes and scenic views
      "Mambusao", // Gateway to Burias Island and its white sand beaches
      "Milagros", // Town known for its fish sanctuaries and mangrove forests
      "Moises Padrilla", // Town known for its waterfalls and caves
      "Palompon", // Town known for its historical landmarks and cultural heritage
      "Pio V. Corvera", // Scenic town with diverse agricultural crops and landscapes
      "San Fernando", // Town known for its hot springs and pilgrimage sites
      "San Jacinto", // Gateway to Ticao Pass and its mesmerizing sandbar
      "San Miguel", // Town known for its rice terraces and traditional crafts
      "San Pascual", // Scenic town with hidden coves and waterfalls
      "Uson", // Town known for its historical landmarks and scenic views
    ],
    "Misamis Occidental": [
      "Oroquieta City", // Provincial capital
      "Alubijid",
      "Balingasag",
      "Balingoan",
      "Bonifacio",
      "Calamba",
      "Clarin",
      "Concepcion",
      "Don Victoriano Chiongbian",
      "Gingoog City",
      "Glendale",
      "Jimenez",
      "Lopez Jaena",
      "Lourdes",
      "Loyola",
      "Magsaysay",
      "Medina",
      "Miamis Oriental",
      "Moraan",
      "Oliva",
      "Ozamis City",
      "Palanca",
      "Salinas",
      "Sapang Dalaga",
      "Sinacaban",
      "Tangub City",
      "Tudela",
    ],
    "Misamis Oriental": [
  "Cagayan de Oro", // Provincial capital and economic hub
  "Alubijid", // Town known for its hot springs and scenic landscapes
  "Balingoan", // City known for its eco-tourism attractions
  "Balingasag", // Town featuring historical landmarks and the Balamban River
  "Baller", // Town known for its caves and the Balingoan Falls
  "Bonifacio", // Town known for its agricultural lands and rice terraces
  "Calaan, El Salvador", // Municipality famous for its white sand beaches
  "Claveria", // Town rich in cultural heritage and known for its Abaca industry
  "Gingoog City", // City known for its waterfalls and white water rafting
  "Gitagum", // Town known for its pineapple plantations and agricultural products
  "Initao", // Town featuring historical churches and the Balatukan Range
  "Jasaan", // Town known for its caves and hot springs
  "Kinoguitan", // Town known for its rice terraces and scenic landscapes
  "Lagonglong", // Municipality famous for its white sand beaches and diving spots
  "Laguindingan", // Town known for its historical landmarks and the Balingoan River
  "Libertad", // Town known for its rice terraces and agricultural products
  "Lugait", // Town known for its hot springs and waterfalls
  "Magsaysay", // Municipality famous for its white sand beaches and historical sites
  "Malitbog", // Town known for its caves and cultural heritage
  "Manticao", // Municipality known for its white sand beaches and diving spots
  "Medina", // Town known for its rice terraces and agricultural products
  "Opol", // Town featuring historical landmarks and the Opol River
  "Oroquieta City", // City known for its waterfalls and the Danao River
  "Salay", // Town known for its hot springs and scenic landscapes
  "Sugbongcogon", // Town known for its rice terraces and agricultural products
  "Talisay", // Town known for its caves and historical landmarks
  "Tangub City", // City known for its white sand beaches and the Tangub River
  "Villanueva", // Town known for its agricultural lands and historical sites
],
"Mountain Province": [
    "Bontoc", // Provincial capital and home to rice terraces
    "Benguet", // Known for its scenic landscapes and Baguio City
    "Ifugao", // Rich in indigenous culture and rice terraces
    "Kalinga", // Rugged terrain with diverse indigenous tribes
    "Apayao", // Home to the Ifugao and Kalinga ethnic groups
  ],
  "Negros Occidental": [
      "Bacolod", // Provincial capital
      "Bago City", // Known for its heritage sites and food specialties
      "Cadiz City", // Gateway to Danjugan Island and its marine sanctuary
      "Escalante City", // Home to the Sugarcane Festival and agri-tourism sites
      "Himamaylan City", // Known for its hot springs and ancestral mansions
      "Kabankalan City", // Gateway to Mt. Kanlaon Natural Park and waterfalls
      "La Carlota City", // Home to the Panaad Festival and sugar plantations
      "Silay City", // Gateway to the Island of Guimaras and historical landmarks
      "Sipalay City", // Known for its diving spots and adventure activities
      "Talisay City", // Popular eco-tourism destination with diverse attractions
      "Victorias City", // Home to the Grand Prix Motorcycle Racing and heritage sites
      "Abangay", // Town known for its heritage houses and traditional crafts
      "Binalbagan", // Gateway to Balanan, a birdwatching paradise
      "Calatrava", // Town known for its waterfalls and agricultural lands
      "Candoni", // Home to the Manggis Festival and agricultural landscapes
      "Cauayan", // Gateway to Sipalay and its natural wonders
      "Enrique B. Magalona", // Town known for its beaches and diving spots
      "Ginigaran", // Home to the Pintaflores Festival and historical structures
      "Hinoba-an", // Gateway to Danjugan Island and its marine sanctuary
      "Hinigaran", // Town known for its rice terraces and cultural heritage
      "Ilog", // Home to the Dinagyang Festival and historical landmarks
      "Isabela", // Town known for its beaches and marine reserve
      "Jimalalud", // Town known for its hot springs and mountain scenery
      "La Castellana", // Home to the Panaad Festival and sugar plantations
      "La Paz", // Town known for its ancestral mansions and rice terraces
      "Llaneta", // Town known for its heritage sites and waterfalls
      "Magallon", // Home to the Manggahan Festival and fruit orchards
      "Moises Padilla", // Town known for its rice terraces and waterfalls
      "Murcia", // Home to the Magsaysay Festival and historical landmarks
      "Pontevedra", // Town known for its beaches and seafood specialties
      "Pulau", // Town known for its historical landmarks and cultural heritage
      "San Enrique", // Town known for its rice terraces and fruit orchards
      "Siquijor", // Town known for its caves and natural attractions
      "Toboso", // Gateway to Mt. Kanlaon Natural Park and hiking trails
      "Valladolid", // Town known for its rice terraces and agricultural landscapes
      "Valenzuela", // Town known for its beaches and coastal landscapes
    ],
    "Negros Oriental": [
      "Bacolod", // Provincial capital and economic center
      "Bayawan", // City known for its waterfalls and hot springs
      "Canlaon City", // City known for its geothermal power plant and mountain scenery
      "Dumaguete", // University town and tourist destination with diving and cultural attractions
      "Guihulngan", // City known for its rice terraces and historical landmarks
      "Siquijor", // Island municipality famous for its mysticism and natural beauty
      "Tanjay", // City known for its beaches and marine sanctuaries
      "Amlan", // Town known for its sugarcane plantations and heritage homes
      "Ayungon", // Town known for its rice terraces and waterfalls
      "Bacong", // Town known for its beaches and hot springs
      "Basay", // Town known for its historical landmarks and natural caves
      "Dauin", // Town known for its diving spots and whale shark encounters
      "Jimalalud", // Town known for its waterfalls and rice terraces
      "La Libertad", // Town known for its sugarcane plantations and heritage churches
      "Larena", // Town known for its beaches and marine sanctuaries
      "Mabinay", // Town known for its rice terraces and waterfalls
      "Manjuyod", // Town known for its bamboo handicrafts and waterfalls
      "Nalongvan", // Town known for its rice terraces and mountain scenery
      "San Jose", // Town known for its beaches and diving spots
      "Santa Catalina", // Town known for its historical landmarks and waterfalls
      "Siaton", // Town known for its beaches and marine sanctuaries
      "Tayasan", // Town known for its rice terraces and mountain scenery
      "Valencia", // Town known for its hot springs and natural attractions
      "Valladolid", // Town known for its rice terraces and waterfalls
    ],
    "Northern Samar": [
      "Allen",
      "Baller",
      "Biri",
      "Bobon",
      "Capalungan",
      "Catarman", // Provincial capital
      "Catubig",
      "Gamay",
      "Las Navas",
      "Laoang",
      "Mapanas",
      "Mondragon",
      "Palapag",
      "Pambujan",
      "Rosario",
      "San Isidro",
      "San Lorenzo",
      "San Roque",
      "Santa Elena",
      "Silvino Lobos",
      "Victoria",
    ],
    "Nueva Ecija": [
  "Cabatuan", // Provincial capital and economic center
  "Aliaga", // Town known for its rice terraces and mango plantations
  "Bongabon", // Gateway to the Sierra Madre mountain range
  "Cabanasan", // Town known for its hot springs and waterfalls
  "Caragan", // Scenic town with diverse flora and fauna
  "Cuyapo", // Home to the Bunu Festival and historical landmarks
  "Gapan", // Town known for its agricultural lands and cultural heritage
  "General Mamerto", // Gateway to the Minalungao National Park
  "General Tinio", // Historical town with Spanish colonial architecture
  "Guimba", // Town known for its rice terraces and fruit orchards
  "Jaen", // Home to the Carabao Festival and traditional crafts
  "Laur", // Scenic town with waterfalls and caves
  "Licuan-Baay", // Coastal town with pristine beaches
  "Llanera", // Home to the Carabao Festival and traditional weaving
  "Lucena", // Town known for its historical landmarks and agricultural lands
  "Nampacpacan", // Scenic town with mountains and rice terraces
  "Pangasinan", // Town known for its hot springs and waterfalls
  "Peñaranda", // Gateway to the Angat Dam and its recreational activities
  "Quezon", // Town known for its historical landmarks and religious sites
  "Rizal", // Home to the Bambanti Festival and traditional crafts
  "San Antonio", // Scenic town with mountains and waterfalls
  "San Isidro", // Gateway to the Pantabangan Dam and its scenic views
  "Santa Cruz", // Historical town with Spanish colonial architecture
  " Talavera", // Town known for its fruit orchards and rice terraces
  "Talugtog", // Home to the Bunu Festival and indigenous traditions
  "Zaragoza", // Town known for its historical landmarks and agricultural lands
],
"Nueva Vizcaya": [
      "Alfonso Castañeda",
      "Ambaguio",
      "Aritao",
      "Bagabag",
      "Bambang",
      "Bayombong",
      "Diadi",
      "Dupax del Norte",
      "Dupax del Sur",
      "Kasibu",
      "Kayapa",

      
"Quezon",
      "Santa Fe",
      "Solano",
      "Villaverde",
    ],
    "Occidental Mindoro": [
      "Sablayan", // Provincial capital
      "Calintaan", // Scenic town known for Apo Reef Natural Park
      "San Jose", // Gateway to Mangrove forests and marine sanctuaries
      "Magsaysay", // Town known for its waterfalls and caves
      "Alcantara", // Home to the Halcon River and rice terraces
      "Santa Cruz", // Town surrounded by mountains and rice paddies
      "Buenavista", // Rich in biodiversity with diverse marine life
      "Abra de Ilog", // Known for its beaches and sand dunes
      "Mamburao", // Town with historical landmarks and cultural heritage
      "Paluan", // Island municipality famous for its white sand beaches and coral reefs
    ],
    "Oriental Mindoro": [
  "Baco", // Historical town with Spanish colonial architecture
  "Bansud", // Home to the Mangyan tribe
  "Bongabong", // Known for its waterfalls and caves
  "Bulalacao", // Southernmost municipality with pristine beaches
  "Calapan", // Provincial capital
  "Gloria", // Mountainous region with agricultural lands
  "Mansalay", // Surfing destination with diverse marine life
  "Naujan", // Home to Lake Naujan, the largest freshwater lake in Mindoro
  "Pinamalayan", // Largest municipality in Oriental Mindoro
  "Pola", // Scenic coastal town with hidden coves
  "Puerto Galera", // Popular tourist destination
  "Roxas", // Town surrounded by mountains and rice paddies
  "San Teodoro", // Known for beaches and snorkeling
  "Socorro", // Known for its mangrove forests and fish sanctuaries
  "Victoria", // Gateway to Apo Reef Natural Park
],
"Palawan": [
  "Aborlan",
  "Agutaya",
  "Araceli",
  "Balabac",
  "Bataraza",
  "Brooke's Point",
  "Busuanga",
  "Cagayancillo",
  "Coron",
  "Culion",
  "Cuyo",
  "Dumaran",
  "El Nido",
  "Kalayaan",
  "Linapacan",
  "Magsaysay",
  "Narra",
  "Quezon",
  "Rizal",
  "Roxas",
  "San Vicente",
  "Sofronio Española",
  "Taytay",
],
"Pampanga": [
  "Apalit",
  "Arayat",
  "Bacolor",
  "Candaba",
  "Floridablanca",
  "Guagua",
  "Lubao",
  "Macabebe",
  "Magalang",
  "Masantol",
  "Mexico",
  "Minalin",
  "Porac",
  "San Luis",
  "San Simon",
  "Santa Ana",
  "Santa Rita",
  "Santo Tomas",
  "Sasmuan",
],
"Pangasinan": [
  "Alaminos",
  "Alcala",
  "Anda",
  "Asingan",
  "Balungao",
  "Banguet",
  "Baung",
  "Bayambang",
  "Binmaley",
  "Capas",
  "Dagupan",
  "Dasol",
  "Infanta",
  "Lingayen", // Provincial capital
  "Mabini",
  "Malasiqui",
  "Mangatarem",
  "Mangayan",
  "San Carlos",
  "San Fabian",
  "San Jacinto",
  "San Manuel",
  "Santa Barbara",
  "Santa Maria",
  "Sison",
  "Tayug",
  "Umingan",
  "Urbiztondo",
  "Villasis",
],
"Quezon": [
  "Agdangan",
  "Alabat",
  "Atimonan",
  "Buenavista",
  "Burdeos",
  "Calauag",
  "Candelaria",
  "Catanauan",
  "Dolores",
  "General Luna",
  "General Nakar",
  "Guinayangan",
  "Gubat",
  "Gumaca",
  "Infanta",
  "Jomalig",
  "Lopez",
  "Lucban",
  "Macalelon",
  "Mauban",
  "Mulanay",
  "Padre Burgos",
  "Pagbilao",
  "Panukulan",
  "Patnanungan",
  "Perez",
  "Pitogo",
  "Plaridel",
  "Polillo",
  "Quezon",
  "Real",
  "Sampaloc",
  "San Andres",
  "San Antonio",
  "San Francisco",
  "San Narciso",
  "Sariaya",
  "Tagkawayan",
  "Tiaong",
  "Unisan",
],
"Quirino": [
  "Cabagan", // Provincial capital
  "Diffun",
  "Maddela",
  "Nagtipunan",
  "Saguday",
  "Siguiran",
],
"Rizal": [
  "Angono",
  "Antipolo City",
  "Baras",
  "Binangonan",
  "Cainta",
  "Cardona",
  "Jala-Jala",
  "Lopez",
  "Marikina City",
  "Masigla",
  "Montalban",
  "Morong",
  "Navotas City",
  "Pateros City",
  "San Mateo",
  "Tanay",
  "Taytay",
  "Teresa",
],
"Romblon": [
  "Banton", // Island municipality known for its diving sites
  "Cajidiocan", // Town with limestone formations and hot springs
  "Calatrava", // Town known for its Spanish colonial architecture
  "Concepción", // Town with rich cultural heritage and waterfalls
  "Cordoba", // Town known for its beaches and sandbars
  "Ferrol", // Town with scenic islands and caves
  "Looc", // Town known for its mangroves and marine sanctuaries
  "Magdiwang", // Town with historical landmarks and rice terraces
  "Odiongan", // Island municipality and gateway to Romblon Island
  "Romblon", // Provincial capital and island municipality
  "San Agustin", // Town known for its caves and waterfalls
  "San Andres", // Town with white sand beaches and marine life
  "San Fernando", // Town known for its agricultural lands and scenic views
  "San Jose", // Town known for its hot springs and rice terraces
  "Santa Catalina", // Town with diverse marine life and coral reefs
  "Santa Maria", // Town known for its mangroves and coastal communities
  "Tablas", // Island municipality and gateway to Tablas Island
  "Tuguegarao", // Town known for its sandbars and fishing villages
],
"Samar": [
  // A
  "Albuera", // Town known for its beaches and the Balangiga Massacre Historical Site
  "Allen", // Town known for its hot springs and historical landmarks
  "Calbayog", // City known as the "Gateway to Eastern Visayas"
  "Catbalogan", // Provincial capital of Samar
  // C
  "Catol", // Town known for its eco-tourism activities and waterfalls
  "Concepcion", // Town known for its historical churches and heritage houses
  "Gandara", // Town known for its rice terraces and scenic landscapes
  // G
  "Giporlos", // Town known for its diverse marine life and pristine beaches
  "Guinobatan", // Town known for its agricultural lands and traditional crafts
  // L
  "La Loma", // Town known for its waterfalls and caves
  "Las Mercedes", // Town known for its rice terraces and religious landmarks
  "Lavezares", // Town known for its hot springs and historical landmarks
  // O
  "Oras", // Town known for its beaches and natural attractions
  "Paguay", // Town known for its rice terraces and scenic landscapes
  "Palo", // Town known for its historical landmarks and archaeological sites
  "Pambujan", // Town known for its mangroves and marine sanctuaries
  // S
  "San Isidro", // Town known for its rice terraces and traditional crafts
  "San Jorge", // Town known for its beaches and island hopping activities
  "San Jose de Buan", // Town known for its waterfalls and caves
  "San Sebastian", // Town known for its historical churches and heritage houses
  "Santa Margarita", // Town known for its rice terraces and scenic landscapes
  "Santa Rita", // Town known for its hot springs and historical landmarks
  "Soria", // Town known for its rice terraces and natural attractions
  // T
  "Talale", // Town known for its beaches and marine sanctuaries
  "Taft", // Town known for its rice terraces and scenic landscapes
  "Tuguegarao", // Town known for its historical landmarks and archaeological sites
  // V
  "Victoria", // Town known for its rice terraces and agricultural lands
  "Villareal", // Town known for its hot springs and historical landmarks
],
"Sarangani": [
      "Alabel", // Provincial capital
      "Glan",
      "Kiamba",
      "Maasim",
      "Malapatan",
      "Malungon",
      "Sigaboy",
    ],
    "Siquijor": [
      "Guiwanon",
      "Hagna",
      "Ipil",
      "Lazi",
      "Lugo",
      "Lutopan",
      "Malahide",
      "Nabulao",
      "Old Poblacion...", // Add the remaining barangays of Siquijor town here
    ],
    "Sorsogon": [
  "Barcelona",
  "Bulan",
  "Casiguran",
  "Castilla",
  "Gubat",
  "Irosin",
  "Juban",
  "Magallanes",
  "Matnog",
  "Pili",
  "Prieto Diaz",
  "Sorsogon City",
  "Santa Magdalena",
  "Sorsogon",
  "Tigaon",
],
"South Cotabato": [
  "Alabele",
  "Banga",
  "General Santos City", // Independent City within South Cotabato
  "Lake Sebu",
  "Lutayan",
  "Maasim",
  "Maitum",
  "Malapatan",
  "Norala",
  "Polomolok",
  "T'boli",
  "Tampakan",
  "Tantangan",
  "Tupi",
],
"Southern Leyte": [
      "Anahawan",
      "Bontoc",
      "Cabalian",
      "Caibiran",
      "Dahican",
      "David",
      "Dimasangcay",
      "Hinunangan",
      "Liloan",
      "Limasawa",
      "Maasin (capital)",
      "Macrohon",
      "Malitbog",
      "Niños Fríos",
      "Sogod",
      "Tomas Lopez",
    ],
    "Sultan Kudarat": [
  "Bagumbong",
  "Columbio",
  "Isabela",
  "Kalamansig",
  "Lambayong",
  "Lebeng",
  "Lual",
  "Magsaysay",
  "Matanog",
  "Palimbang", // Provincial capital
  "President Roxas",
  "Quezón",
  "Senator Ninoy Aquino",
  "Shariff Saydona Mustapha",
  "Taft",
  "Tampakan",
  "Tantawan",
  "Tulunan",
],
"Sulu": [
      "Banguingui",
      "Hadji Panglima Tahil",
      "Indanan",
      "Jolo", // Provincial capital
      "Kalingalang Tubig",
      "Lugus",
      "Maimbung",
      "Old Panamao",
      "Omar",
      "Pandami",
      "Panglima Hadji Mohammad",
      "Parang",
      "Patul",
      "Pinang, Sulu",
      "Talipao",
      "Tapul",
    ],
    "Surigao del Norte": [
  "Alegria",
  "Bacuag",
  "Burgos",
  "Claver",
  "Dapa",
  "Del Carmen",
  "General Luna",
  "Gigaquit",
  "Mainit",
  "Malimono",
  "Pilar",
  "Placer",
  "San Benito",
  "San Francisco",
  "San Isidro",
  "Sison",
  "Socorro",
  "Sta. Monica",
  "Surigao City", // Provincial capital
  "Tagana-an",
  "Tubod",
],
"Surigao del Sur": [
  "Barobo",
  "Bayabas",
  "Cagwait",
  "Cantilan",
  "Carmen",
  "Carrascal",
  "Cortes",
  "Hinatuan",
  "Lanuza",
  "Lianga",
  "Lingig",
  "Madrid",
  "Marihatag",
  "San Agustin",
  "San Miguel",
  "Tagbina",
  "Tago"
],
"Tarlac": [
  "Anao",
  "Bamban",
  "Camiling",
  "Capas",
  "Concepcion",
  "Gerona",
  "La Paz",
  "Mayantoc",
  "Moncada",
  "Paniqui",
  "Pura",
  "Ramos",
  "San Clemente",
  "San Jose",
  "San Manuel",
  "Santa Ignacia",
  "Tarlac City", // City, not municipality
  "Victoria",
],
"Tawi-Tawi": [
      "Bongao",  // Provincial capital
      "Languyan",
      "Mapun",
      "Panglima Sugala",
      "Simunul",
      "Sibutu",
      "Sitangkai",
      "South Ubian",
      "Tandubas",
      "Turtle Islands"
    ],
    "Zambales": [
  "Botolan",
  "Cabangan",
  "Castillejos",
  "Iba (Capital)",
  "Masinloc",
  "Olongapo",
  "Palauig",
  "San Antonio",
  "San Felipe",
  "San Marcelino",
  "San Narciso",
  "Santa Cruz",
  "Subic"
],
"Zamboanga del Norte": [
  "Dapitan City",
  "Dipolog City",
  "Katipunan",
  "La Libertad",
  "Labason",
  "Liloy",
  "Manukan",
  "Mutia",
  "Polanco",
  "President Manuel A. Roxas",
  "Rizal",
  "Salug",
  "Sergio Osmeña Sr.",
  "Siayan",
  "Sibuco",
  "Sibutad",
  "Sindangan",
  "Siocon",
  "Tampilisan",
],
"Zamboanga del Sur": [
  "Aurora",
  "Bayog",
  "Dimataling",
  "Dinas",
  "Dumalinao",
  "Dumingag",
  "Guipos",
  "Josefina",
  "Kumalarang",
  "Labangan",
  "Lakewood",
  "Lapuyan",
  "Mahayag",
  "Margosatubig",
  "Midsalip",
  "Molave",
  "Pitogo",
  "Ramon Magsaysay",
  "San Miguel",
  "San Pablo",
  "Sominot",
  "Tabina",
  "Tambulig",
  "Tigbao",
  "Tukuran",
  "Vincenzo A. Sagun"
],
"Zamboanga Sibugay": [
      "Alicia",
      "Buug",
      "Diplahan",
      "Imelda",
      "Ipil",
      "Kabasalan",
      "Mabuhay",
      "Malangas",
      "Naga",
      "Olutanga",
      "Payao",
      "Roseller Lim",
      "Siay",
      "Talusan",
      "Titay",
    ],

    };
    this.barangaysByCity = {
      "Calapan": [
        "Balingayan",
        "Balite",
        "Baruyan",
        "Batino",
        "Bayanan I",
        "Bayanan II",
        "Biga",
        "Bondoc",
        "Bucayao",
        "Buhuan",
        "Bulusan",
        "Calero",
        "Camansihan",
        "Camilmil",
        "Canubing I",
        "Canubing II",
        "Comunal",
        "Guinobatan",
        "Gulod",
        "Gutad",
        "Ibaba East",
        "Ibaba West",
        "Ilaya",
        "Lalud",
        "Lazareto",
        "Libis",
        "Lumang Bayan",
        "Mahal na Pangalan",
        "Maidlang",
        "Malad",
        "Malamig",
        "Managpi",
        "Masipit",
        "Nag-iba I",
        "Nag-iba II",
        "Navotas",
        "Pachoca",
        "Palhi",
        "Panggalaan",
        "Parang",
        "Patas",
        "Personas",
        "Putingtubig",
        "Salong",
        "San Antonio",
        "San Vicente Central",
        "San Vicente East",
        "San Vicente North",
        "San Vicente South",
        "San Vicente West",
        "Santa Cruz",
        "Santa Isabel",
        "Santa Maria Village",
        "Santa Rita",
        "Santo Niño",
        "Sapul",
        "Silonay",
        "Suqui",
        "Tawagan",
        "Tawiran",
        "Tibag",
        "Wawa"
      ],
      // ... (add data for all provinces)
    };
  },
  methods: {
    fetchCities() {
      this.cities = this.citiesByProvince[this.selectedProvince];
    },
    fetchBarangays() {
      // Make sure that this.selectedCity is defined before accessing barangaysByCity
      if (this.selectedCity) {
        this.barangays = this.barangaysByCity[this.selectedCity] || [];
      } else {
        this.barangays = [];
      }
    },
  },
};
</script>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  display: grid;
  height: 100vh;
  place-items: center;
  background: #2b2b2b;
}

.checkbox{
  height: 160px;
  width: 320px;
  background: #222;
  appearance: none;
  border-radius: 160px;
  box-shadow: inset 0 8px 60px rgba(0,0,0,0.1),
              inset 0 8px 8px rgba(0,0,0,0.1),
              inset 0 -4px 4px rgba(0,0,0,0.1);
  position: relative;
  outline: none;
  cursor: pointer;
  transition: 0.5s;            
}

.checkbox::before{
  height: 160px;
  width: 160px;
  position: absolute;
  top: 0;
  left: 0;
  content: "";
  background: linear-gradient(to bottom,#444,#222);
  border-radius: 160px;
  transform: scale(0.9);
  transition: 0.5s;
  box-shadow: 0 8px 40px rgba(0,0,0,0.5),
              inset 4px 4px rgba(255,255,255,0.2),
              inset -4px 4px rgba(255,255,255,0.2);
}

.checkbox:checked{
  background: #fff;
  box-shadow: inset 0 2px 60px rgba(0,0,0,0.1),
              inset 0 2px 8px rgba(0,0,0,0.1),
              inset 0 -4px 4px rgba(0,0,0,0.05);
}

.checkbox:checked::before{
  left: 160px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.1),
              inset 4px 4px rgba(255,255,255,1),
              inset -4px 4px rgba(255,255,255,1);
  background: linear-gradient(to bottom,#eaeaea,#f9f9f9);            
}

.checkbox::after{
  content: "";
  position: absolute;
  height: 100vh;
  width: 100vw;
  background: #2b2b2b;
  top: 80px;
  left: 160px;
  z-index: -1;
  transform: translate(-50%,-50%);
  transition: 0.5s;
}

.checkbox:checked::after{
  background: #f8f8f8;
}
</style>