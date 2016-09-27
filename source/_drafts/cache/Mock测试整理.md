1.0  什么是mock测试，什么是mock对象

先来看看下面这个示例：


从上图可以看出如果我们要对A进行测试，那么就要先把整个依赖树构建出来，也就是BCDE的实例。

一种替代方案就是使用mocks


从图中可以清晰的看出
mock对象就是在调试期间用来作为真实对象的替代品。
mock测试就是在测试过程中，对那些不容易构建的对象用一个虚拟对象来代替测试的方法就叫mock测试。
2.0  mockito简介
我们选用mockito作为mock框架
依赖jar
<dependency>
 <groupId>org.mockito</groupId>
 <artifactId>mockito-all</artifactId>
 <version>1.9.5</version>
 <scope>test</scope>
</dependency>
2.1 为了使代码更简洁，最好在测试类中导入静态资源
import static org.mockito.Mockito.*;  
import static org.junit.Assert.*;  
2.2 Hello World
// MockitoJUnitRunner 会将需要依赖的服务(@Mock)注入到实际调用服务(@InjectMocks)中
@RunWith(MockitoJUnitRunner.class)
public class ReasonServiceImplTest {
    // 需要调用的服务
    @InjectMocks
    private ReasonServiceImpl reasonServiceImpl = new ReasonServiceImpl();
    // 模拟服务
    @Mock
    private ReasonCacheStorage reasonCacheStorage;
    @Mock
    private ReasonStorage reasonStorage;

    @Test
    public void findValidReason() {
        // 创建对象
        List<ReasonDO> reasons = new ArrayList<>();
        ReasonDO reason1 = new ReasonDO();
        reason1.setCode("code1");
        reason1.setreason("取消订单原因1");
        reasons.add(reason1);
        ReasonDO reason2 = new ReasonDO();
        reason2.setCode("code2");
        reason2.setreason("取消订单原因2");
        reasons.add(reason2);
        // 预设当原因类型为订单取消时返回创建的对象
        when(reasonCacheStorage.find(ReasonType.MEMBER_CLOSE_ORDER)).thenReturn(reasons);
        // 调用实际服务
        List<ReasonDO> result = reasonServiceImpl.findValidReason(ReasonType.MEMBER_CLOSE_ORDER);
        // 对返回结果进行断言
        assertEquals("订单取消原因集合个数", 2, result.size());
        assertEquals("订单取消原因集合详细内容", "code1", result.get(0).getCode());
    }
}
依赖的服务代码示例
public class ReasonServiceImpl{
@Override
public List<ReasonDO> findValidReason(int reasonType) {
   List<ReasonDO> list = reasonCacheStorage.find(reasonType);
   if(CollectionUtil.isEmpty(list)){
      list = reasonStorage.findValidReason(reasonType);
      // 将原因类型集合放入缓存
      reasonCacheStorage.add(list);
   }
   return list;
}
}
3.0 mockito的部分api示例
3.1 验证行为
 
@Test  
public void verify_behaviour(){  
    //模拟创建一个List对象  
    List mock = mock(List.class);  
    //使用mock的对象  
    mock.add(1);  
    mock.clear();  
    //验证add(1)和clear()行为是否发生  
    verify(mock).add(1);  
    verify(mock).clear();  
}
 
3.2 模拟我们所期望的结果
 
@Test  
public void when_thenReturn(){  
    //mock一个Iterator类  
    Iterator iterator = mock(Iterator.class);  
    //预设当iterator调用next()时第一次返回hello，第n次都返回world  
    when(iterator.next()).thenReturn("hello").thenReturn("world");  
    //使用mock的对象  
    String result = iterator.next() + " " + iterator.next();  
    //验证结果  
    assertEquals("hello world",result);  
}
 
3.3 验证调用次数
 
@Test  
public void verifying_number_of_invocations(){  
    List list = mock(List.class);  
    list.add(1);  
    list.add(2);  
    list.add(2);  
    list.add(3);  
    list.add(3);  
    list.add(3);  
    //验证是否被调用一次，等效于下面的times(1)  
    verify(list).add(1);  
    verify(list,times(1)).add(1);  
    //验证是否被调用2次  
    verify(list,times(2)).add(2);  
    //验证是否被调用3次  
    verify(list,times(3)).add(3);  
    //验证是否从未被调用过  
    verify(list,never()).add(4);  
    //验证至少调用一次  
    verify(list,atLeastOnce()).add(1);  
    //验证至少调用2次  
    verify(list,atLeast(2)).add(2);  
    //验证至多调用3次  
    verify(list,atMost(3)).add(3); 
3.4 模拟方法体抛出异常
 
@Test(expected = RuntimeException.class)  
public void doThrow_when(){  
    List list = mock(List.class);  
    doThrow(new RuntimeException()).when(list).add(1);  
    list.add(1);  
} 
3.5 验证执行顺序
 
@Test  
public void verification_in_order(){  
    List list = mock(List.class);  
    List list2 = mock(List.class);  
    list.add(1);  
    list2.add("hello");  
    list.add(2);  
    list2.add("world");  
    //将需要排序的mock对象放入InOrder  
    InOrder inOrder = inOrder(list,list2);  
    //下面的代码不能颠倒顺序，验证执行顺序  
    inOrder.verify(list).add(1);  
    inOrder.verify(list2).add("hello");  
    inOrder.verify(list).add(2);  
    inOrder.verify(list2).add("world");  
}  
3.6 捕获器
/* 构建ArgumentCaptor对象，捕获器 */@Captor
private ArgumentCaptor<Pagination> paginationArgumentCaptor;

verify(reviewProvider).find(paginationArgumentCaptor.capture());
// 获取捕获的参数
Pagination captorPagination = paginationArgumentCaptor.getValue();



