# listarClientes
Listar N clientes de una bdd SQL  

class cliente_search(APIView):
def get(self, request):
        clientes = Cliente.objects.using('clientes').all()[:1]
        serializer_cliente = ClienteSerializer(clientes, many=True)
        serializer_cliente = agg_catalogos_cliente(serializer_cliente.data)
        return Response({"data":serializer_cliente}, status=status.HTTP_200_OK)
