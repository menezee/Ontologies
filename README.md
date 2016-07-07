# Ontologies

Ontology for public transportation domain modeled in Protégé <http://protege.stanford.edu/>.
transportationJourneyPlanner.owl

Mapped classes:

	Passageiro
		Adulto
		Idoso
	Rota
		Calçada
		CorredorDeOnibus
		Rua
	Terminal
		PontoDeLotação
		PontoDeOnibus
		PontoDeTaxi
	TransportePublico
		Bicicleta
		Lotação	
		Onibus
		Taxi

Data properties:
	
	documentosEstãoVencidos
	temLugarDisponivel
	éPassageiroPreferencial

Object properties:

	podeAndarDe
	podePararEm
	podeSerMultado
	seLocomoveEm

Rules:

	TransportePublico(?t), temLugarDisponivel(?t, true), Passageiro(?p) -> podeAndarDe(?p, ?t)
	Onibus(?o), PontoDeOnibus(?p) -> podePararEm(?o, ?p)
	TransportePublico(?p), documentosEstãoVencidos(?p, true) -> podeSerMultado(?p, ?p)
	Lotação(?l), PontoDeLotação(?p) -> podePararEm(?l, ?p)
	Onibus(?b), CorredorDeOnibus(?c) -> seLocomoveEm(?b, ?c)
	Idoso(?i), Onibus(?o), temLugarDisponivel(?o, false), éPassageiroPreferencial(?i, true) -> podeAndarDe(?i, ?o)
	Taxi(?t), PontoDeTaxi(?p) -> podePararEm(?t, ?p)
	Adulto(?a), Bicicleta(?b) -> podeAndarDe(?a, ?b)
	Passageiro(?p), Onibus(?o), temLugarDisponivel(?o, true) -> podeAndarDe(?p, ?o)
	Bicicleta(?h), Calçada(?y) -> seLocomoveEm(?h, ?y)