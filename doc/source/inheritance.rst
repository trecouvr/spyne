===========
Inheritance
===========



.. code:: python

    class A(ServiceBase):
        @rpc(String, _returns=String, _no_cls=False)
        def hello(cls, ctx, name):
            print(name, cls)
            return cls._hello(name)

        @classmethod
        def _hello(cls, name):
            return 'Hello, %s' % name


    class B(A):
        @classmethod
        def _hello(cls, name):
            return 'Bello, %s' % name


    app = Application([B], name='Service', tns='my.ns.roxx', ..)

    # client
    client.service.hello('tom')
    # >>> Bello, tom
