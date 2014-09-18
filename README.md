Multibooker folder structure

<pre>

multibooker/
	sources/
		application/
			modules/
				addresses/
					controllers/
						addresses.find.controller.coffee
						addresses.create.controller.coffee
						addresses.read.controller.coffee
					addresses.module.coffee
					addresses.router.coffee
				authentication/
					controllers/
						authentication.signin.controller.coffee
						authentication.signout.controller.coffee
					authentication.module.coffee
					authentication.router.coffee
			application.module.coffee
			application.router.coffee
		public/
			assets/
			application/
				modules/
					addresses/
						controllers/
							addresses.collection.controller.coffee
							addresses.document.controller.coffee
							addresses.create.controller.coffee
						templates/
							addresses.collection.template.jade
							addresses.document.template.jade
							addresses.create.template.jade
						styles/
							addresses.styles.styl
							addresses.collection.styles.styl
							addresses.document.styles.styl
							addresses.create.styles.styl
						addresses.module.coffee
						addresses.states.coffee
				filters/
				directives/
				services/
				styles/
					application.styles.styl
					application.print.styles.styl
					application.ie8.styles.styl
				application.module.coffee
				application.configuration.coffee
				application.states.coffee
				application.constants.coffee
			index.jade
	distribution/
		development/
		production/

</pre>

application.module.coffee:

<pre>
express = require 'express'
application = do express
addresses = require './modules/addresses/addresses.module'
authentication = require './modules/authetication/authentication.module'

application.use addresses
application.use authetication

application.listen 3000
</pre>

addresses.module.coffee:

<pre>
express = require 'express'
addresses = module.exports = do express
addressesRouter = './addresses.router'

addresses.use addressesRouter
</pre>

addresses.router.coffee:

<pre>
express = require 'express'
addressesRouter = module.exports = do express.Router
addressesFindController = require './controllers/addresses.find.controller'
addressesCreateController = require './controllers/addresses.create.controller'
addressesReadController = require './controllers/addresses.read.controller'
addressesUpdateController = require './controllers/addresses.update.controller'
addressesDeleteController = require './controllers/addresses.delete.controller'

addressesRouter
	.route '/addresses'
		.get addressesFindController
		.post addressesCreateController

addressesRouter
	.route '/addresses/:addressId'
		.get addressesReadController
		.put addressesUpdateController
		.delete addressesDeleteController
</pre>



















