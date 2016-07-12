This is a forked version of openfl-swiftsuspenders. It is forked because there are lots of things that are missing in the reflector, DescribeTypeRTTIReflector.hx. I only implemented named injection for the public fields and properties, but there's still work needed for method injections.

The injection meta tags should be added as following:

		
		@inject public var foo: TypeA;
		@inject("name=awesomeField") public var myAwesomeField: ITypeB;
		@inject public var bar(get, set): TypeC;
		

The mappings:

		
		injector.map(TypeA).asSingleton();
		injector.map(ITypeB, "awesomeField").toType(TypeB);
		var c: TypeC = new TypeC();
		injector.map(TypeC).toValue(c);
		

For manual injection use: 

		
		var typeA: TypeA = new TypeA();
		injector.injectInto(typeA);
		
