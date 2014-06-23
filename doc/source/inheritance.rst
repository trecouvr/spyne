===========
Inheritance
===========


Composition
===========

.. code:: python

    class A(ServiceBase):
        @srpc(String, _returns=String)
        def hello(name):
            print(name)
            return 'Hello, %s' % name


    class B(ServiceBase):
        @srpc(String, _returns=String)
        def hello2(name):
            print(name)
            return 'Hello, %s' % name


    app = Application([A, B], name='Service', tns='my.ns.roxx', ...)

    # on client
    client.service.hello('tom')
    client.service.hello2('tom')


If there are duplicate method names, sphinx raises an exception.


Subclassing
===========


.. code:: python

    class A(ServiceBase):
        @srpc(String, _returns=String)
        def hello(name):
            print(name)
            return 'Hello, %s' % name

        @srpc(String, _returns=String)
        def hello2(name):
            raise NotImplementedError()


    class B(A):
        @srpc(String, _returns=String)
        def hello2(name):
            print(name)
            return 'Hello, %s' % name


    app = Application([B], name='Service', tns='my.ns.roxx', ...)

    # on client
    client.service.hello('tom')
    client.service.hello2('tom')

