# Class Hierarchy

- java.lang.Object
  - java.util.AbstractCollection<E> (implements java.util.Collection<E>)
    - java.util.AbstractList<E> (implements java.util.List<E>)
      - java.util.AbstractSequentialList<E>
        - java.util.LinkedList<E> (implements java.lang.Cloneable, java.util.Deque<E>, java.util.List<E>, java.io.Serializable
          - tk.airshipcraft.market.api.common.misc.SortedList<T>
- tk.airshipcraft.market.api.economy.events.AccountTransactionEvent (implements tk.airshipcraft.market.api.common.event.Cancellable)
  - tk.airshipcraft.market.api.economy.events.NonPlayerAccountTransactionEvent
  - tk.airshipcraft.market.api.economy.events.PlayerAccountTransactionEvent
- tk.airshipcraft.market.api.common.event.Completion
- tk.airshipcraft.market.api.economy.transaction.EconomyTransaction
- tk.airshipcraft.market.api.economy.transaction.EconomyTransaction.Builder
- tk.airshipcraft.market.api.common.event.EventBus.EventSubscriberBuilder<T>
- tk.airshipcraft.market.api.common.event.EventSubscriber<T> (implements java.lang.Comparable<T>)
  - tk.airshipcraft.market.api.common.event.SimpleEventSubscriber<T>
- tk.airshipcraft.market.api.common.event.FireCompletion<T>
- tk.airshipcraft.market.api.common.misc.FutureHelper
- tk.airshipcraft.market.api.common.service.Service<T> (implements java.lang.Comparable<T>, java.util.function.Supplier<T>)
- tk.airshipcraft.market.api.common.service.event.ServiceRegisteredEvent
- tk.airshipcraft.market.api.common.service.event.ServiceUnregisteredEvent
- java.lang.Throwable (implements java.io.Serializable)
  - java.lang.Exception
    - tk.airshipcraft.market.api.common.response.TreasuryException
      - tk.airshipcraft.market.api.economy.response.EconomyException
    
# Interface Hierarchy
- tk.airshipcraft.market.api.economy.account.Account
  - tk.airshipcraft.market.api.economy.account.NonPlayerAccount
  - tk.airshipcraft.market.api.economy.account.PlayerAccount
- tk.airshipcraft.market.api.common.event.Cancellable
- tk.airshipcraft.market.api.economy.currency.Currency
- tk.airshipcraft.market.api.economy.EconomyProvider
- tk.airshipcraft.market.api.economy.transaction.EconomyTransactionInitiator<T>
- tk.airshipcraft.market.api.common.response.FailureReason
- tk.airshipcraft.market.api.common.response.Subscriber<T,E>
  - tk.airshipcraft.market.api.economy.response.EconomySubscriber<T>

# Enum Hierarchy

- java.lang.Object
  - java.lang.Enum<E> (implements java.lang.Comparable<T>, java.lang.constant.Constable, java.io.Serializable)
    - tk.airshipcraft.market.api.economy.account.AccountPermission
    - tk.airshipcraft.market.api.economy.misc.EconomyAPIVersion
    - tk.airshipcraft.market.api.economy.response.EconomyFailureReason (implements tk.airshipcraft.market.api.common.response.FailureReason)
    - tk.airshipcraft.market.api.economy.transaction.EconomyTransactionImportance
    - tk.airshipcraft.market.api.economy.transaction.EconomyTransactionInitiator.Type
    - tk.airshipcraft.market.api.economy.transaction.EconomyTransactionType
    - tk.airshipcraft.market.api.common.event.EventBus
    - tk.airshipcraft.market.api.common.event.EventPriority
    - tk.airshipcraft.market.api.economy.misc.OptionalEconomyApiFeature
    - tk.airshipcraft.market.api.common.service.ServicePriority
    - tk.airshipcraft.market.api.common.service.ServiceRegistry
    - tk.airshipcraft.market.api.common.misc.TriState