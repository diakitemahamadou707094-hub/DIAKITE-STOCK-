
import 'package:flutter/material.dart';

void main() {
  runApp(const DiakiteStock());
}

class DiakiteStock extends StatelessWidget {
  const DiakiteStock({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'DIAKITE STOCK',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(
          seedColor: const Color(0xFF102C50),
        ),
        useMaterial3: true,
      ),
      home: const Accueil(),
    );
  }
}

class Accueil extends StatelessWidget {
  const Accueil({super.key});

  Widget statistique(
      String titre, String valeur, IconData icone) {
    return Card(
      child: Padding(
        padding: const EdgeInsets.all(12),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Icon(icone, size: 30, color: Colors.blue),
            const SizedBox(height: 8),
            Text(titre),
            const SizedBox(height: 5),
            Text(
              valeur,
              style: const TextStyle(
                fontSize: 18,
                fontWeight: FontWeight.bold,
              ),
            ),
          ],
        ),
      ),
    );
  }

  Widget module(
      BuildContext context, String titre, IconData icone) {
    return Card(
      child: InkWell(
        onTap: () {
          Navigator.push(
            context,
            MaterialPageRoute(
              builder: (_) => PageModule(titre: titre),
            ),
          );
        },
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Icon(icone, size: 32, color: Colors.blue),
            const SizedBox(height: 8),
            Text(titre, textAlign: TextAlign.center),
          ],
        ),
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: const Color(0xFFF0F4F8),
      appBar: AppBar(
        title: const Text('DIAKITE STOCK'),
        backgroundColor: const Color(0xFF102C50),
        foregroundColor: Colors.white,
      ),
      body: ListView(
        padding: const EdgeInsets.all(12),
        children: [
          const Text(
            'Boutique Plus Diakite et Frères',
            style: TextStyle(
              fontSize: 20,
              fontWeight: FontWeight.bold,
            ),
          ),
          const Text('Mahamadou Diakite - Administrateur'),
          const SizedBox(height: 15),
          GridView.count(
            crossAxisCount: 2,
            childAspectRatio: 1.3,
            shrinkWrap: true,
            physics: const NeverScrollableScrollPhysics(),
            children: [
              statistique('Produits', '0', Icons.inventory),
              statistique('Stock', '0 FCFA', Icons.wallet),
              statistique('Ventes', '0 FCFA', Icons.shopping_cart),
              statistique('Bénéfices', '0 FCFA', Icons.trending_up),
            ],
          ),
          const SizedBox(height: 15),
          const Text(
            'Gestion commerciale',
            style: TextStyle(
              fontSize: 20,
              fontWeight: FontWeight.bold,
            ),
          ),
          GridView.count(
            crossAxisCount: 3,
            shrinkWrap: true,
            physics: const NeverScrollableScrollPhysics(),
            children: [
              module(context, 'Produits', Icons.inventory),
              module(context, 'Entrées', Icons.add_box),
              module(context, 'Ventes', Icons.shopping_cart),
              module(context, 'Clients', Icons.people),
              module(context, 'Fournisseurs', Icons.local_shipping),
              module(context, 'Caisse', Icons.wallet),
              module(context, 'Créances', Icons.payments),
              module(context, 'Rapports', Icons.bar_chart),
              module(context, 'Paramètres', Icons.settings),
            ],
          ),
          const SizedBox(height: 20),
          const Center(
            child: Text('DIAKITE STOCK - Version 1.0'),
          ),
        ],
      ),
    );
  }
}

class PageModule extends StatelessWidget {
  final String titre;

  const PageModule({super.key, required this.titre});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(titre),
        backgroundColor: const Color(0xFF102C50),
        foregroundColor: Colors.white,
      ),
      body: Center(
        child: Text(
          'Module $titre\nEn cours de développement',
          textAlign: TextAlign.center,
          style: const TextStyle(fontSize: 20),
        ),
      ),
    );
  }
}
# DIAKITE-STOCK-