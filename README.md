#include <iostream>
#include <cstdlib>
#include <ctime>
#include <iomanip>
#include <locale.h>	
#include <string> 
using namespace std;

int main() {

	string iller[81] = {  "ANKARA", "ADANA", "ADIYAMAN", "AFYONKARAHİSAR", "AĞRI", "AKSARAY", "AMASYA",
"ANTALYA", "ARDAHAN", "ARTVİN", "AYDIN", "BALIKESİR", "BARTIN", "BATMAN", "BAYBURT", "BİLECİK", "BİNGÖL",
"BİTLİS", "BOLU", "BURDUR", "BURSA", "ÇANAKKALE", "ÇANKIRI", "ÇORUM", "DENİZLİ", "DİYARBAKIR", "DÜZCE", "EDİRNE",
"ELAZIĞ", "ERZİNCAN", "ERZURUM", "ESKİŞEHİR", "GAZİANTEP", "GİRESUN", "GÜMÜŞHANE", "HAKKARİ", "HATAY", "IĞDIR",
"ISPARTA","İSTANBUL","İZMİR","KAHRAMANMARAŞ", "KARABÜK", "KARAMAN", "KARS", "KASTAMONU", "KAYSERİ", "KIRIKKALE", "KIRKLARELİ",
"KIRŞEHİR", "KİLİS", "KOCAELİ", "KONYA", "KÜTAHYA", "MALATYA", "MANİSA", "MARDİN", "MERSİN", "MUĞLA", "MUŞ",
"NEVŞEHİR", "NİĞDE", "ORDU", "OSMANİYE", "RİZE", "SAKARYA", "SAMSUN", "SİİRT", "SİNOP", "SİVAS", "ŞIRNAK",
"TEKİRDAĞ", "TOKAT", "TRABZON", "TUNCELİ", "ŞANLIURFA", "UŞAK", "VAN", "YALOVA", "YOZGAT", "ZONGULDAK"
	};


	setlocale(LC_ALL, "Turkish");

	string enKisaİl;
	string enUzunİl;
	
	for (int i = 0; i < 81; i++) {
		string sehir = iller[i];
		if ( enUzunİl.empty()||sehir.size() > enUzunİl.size()) {
			enUzunİl = sehir;
		}
		if (enKisaİl.empty() || sehir.size() <= enKisaİl.size()) {//empty faktörü enKısaİl tanımlayıcısının içini boşaltmak için kullanılır.
			enKisaİl = sehir;
		}
	}

	cout << "En uzun il: " << enUzunİl << endl;
	cout << "En kisa il: " << enKisaİl << endl;
	int şehirdeki_HarfSayısı = 2;

	srand(time(0));

	for (int k = enKisaİl.size(); k < enUzunİl.size(); k++) {
		int sayac = 0;
		string sonuc = "bulunamadı";
		string kullanilanillerSonuc = " ";
		do {
			string* secilenİller = new string[k];
			string kullanilabilenİller;
			for (int i = 0; i < k; i++) {
				secilenİller[i] = iller[rand() % 80+1];
			}

			string Uretilmişİl;
			for (int i = 0; i < k; i++) {
				Uretilmişİl += secilenİller[i].at(0);
				kullanilabilenİller += secilenİller[i];
				kullanilabilenİller += "\t";
			}
			sayac++;

			for (int i = 0; i < 81; i++) {
				string sehir = iller[i];
				if (sehir == Uretilmişİl) {

					sonuc = Uretilmişİl;
					kullanilanillerSonuc = kullanilabilenİller;

				}
			}
		} while (sayac < 100000 && sonuc == "bulunamadı");
		şehirdeki_HarfSayısı++;
		cout << şehirdeki_HarfSayısı << " İndisli Aranan İl :  =  " << sonuc << endl;
		cout << "Kullanılan İller =   " << kullanilanillerSonuc << endl;
	}


}
